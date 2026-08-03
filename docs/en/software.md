# Software

## Architecture

The control logic is centralized and integrates with Home Assistant. The devices (thermostats and manifold) use ESPHome-based firmware, which allows native integration with Home Assistant and flexible configuration.

## Communication

The system uses two communication channels:

| Channel | Protocol | Purpose |
|--------|------------|-------|
| Primary | WiFi + ESPHome API | Configuration, telemetry, commands from Home Assistant |
| Fallback | ESP-NOW | Direct thermostat ↔ manifold communication (no router) |

## Entities exposed in Home Assistant

| Entity | Type | Description |
|--------|------|-------------|
| climate.*_climatizzazione | climate | Thermostat |
| sensor.*_temperatura_reale | sensor | Ambient temperature |
| sensor.*_umidita_reale | sensor | Ambient humidity |
| sensor.*_stato_sistema | sensor | Operating status |
| sensor.*_ultimo_errore | sensor | Last detected error |
| sensor.*_cronologia_errori | sensor | Error history |
| 
umber.*_temperatura_salvata | 
umber | Reference setpoint |
| 
umber.*_soglia_umidita | 
umber | Humidity threshold for operation lock |
| switch.*_modalita_controllata | switch | Enable centralized control |
| utton.*_rinnovo_modalita | utton | Centralized control timer renewal |
| utton.*_reset_allarme_collettore | utton | Manifold alarm reset |
| utton.*_reset_allarme_circolatore | utton | Circulator alarm reset |
| utton.*_reset_errori | utton | Error reset |
| light.*_led_stato | light | Status LED |

## Centralized control logic

### Configurable parameters per zone

| Parameter | Type | Description |
|-----------|------|-------------|
| Weight | Number | Zone importance |
| Inclusion | Boolean | Zone inclusion/exclusion |
| Day standby delta | Number | Standby temperature (day) |
| Night standby delta | Number | Standby temperature (night) |
| Day working delta | Number | Working temperature (day) |
| Night working delta | Number | Working temperature (night) |
| Saved temperature | Number | Reference setpoint |
| Weight threshold | Number | Collective activation threshold |

### Decision flow

1. **Data collection:** real temperature, setpoint, action, mode for each zone
2. **Demand calculation:** for each zone, standby = setpoint - standby_delta; if temp <= standby - 0.5 → requests heat; sum weights
3. **Priority:** zones already running have priority
4. **Collective decision:** if sum_weights >= weight_threshold → activate all
5. **Individual emergency:** if temp <= standby - 0.4 → activate single zone
6. **Execution:** set working setpoint for zones to activate, standby setpoint for zones to deactivate

## LED signaling

Signaling varies depending on configuration and can be customized. As an example:

| State | Typical signal |
|-------|---------------------|
| Active operation | Solid color |
| Standby | Different solid color |
| Minor issues | Slow blinking |
| Critical errors | Fast blinking |
| Alarms | Specific blinking |

Signaling functions are configurable and can be adapted to your needs.
