# The System

## How it fits in the home

This system does not replace the traditional system. It works alongside it.

The traditional system continues to operate in parallel. In case of smart system failure, simply turn it off and the traditional system takes over. For non-technical people: just turn it off, nothing to understand.

This is a huge advantage over closed commercial systems.

The system was born for an underfloor system with an on/off heat pump, divided into multiple zones, but the idea is applicable to other systems: traditional radiators, mixed systems, air conditioners. Any HVAC system that can be controlled by a thermostat.

## The control logic

The heart of the system is a logic that collectively decides when to turn on the heat pump.

Each zone has a weight (importance: area, heat loss, priority). Each zone has deltas: a standby temperature and a working temperature, separated by day and night. A centralized control system calculates the aggregated demand every minute. If the demand exceeds a threshold, the pump turns on. If a zone is already heating, it has priority.

The result is that the heat pump does not turn on for a single small zone, but only when the overall demand is sufficient. Cycles are longer and less frequent. Lower consumption, less wear, more comfort.

## Why this project is different

This system addresses the problem in its entirety, much more than many solutions currently on the market. It is not a simple WiFi thermostat, not a closed system, not an amateur prototype. It is a complete, replicable, structured system with a professional footprint.

**Clarification:** This project was born out of passion, not for profit. I have no interest in commercializing it directly or profiting from it. However, I am well aware that, due to its completeness and robustness, it could lend itself to professional or commercial use. If someone wanted to use it in this sense — for a condominium system, a public building, a hotel, a new construction — they are free to do so. The project is documented, modular, flexible, and the open source license allows it.

Anyone who wants to install it in a professional context can do so. It can manage multiple zones, integrate photovoltaics, communicate without WiFi, operate alongside a traditional system. It is not a product, but it has the structure to become one. And if someone wants to turn it into a product, they have every right to do so, within the terms of the license.
