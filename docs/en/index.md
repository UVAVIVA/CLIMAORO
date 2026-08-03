# CLIMAORO

**Open Source Zonal HVAC Control System**

CLIMAORO is a complete system for centralized heating and cooling control in buildings with underfloor heating and heat pumps, but adaptable to all types of systems. Designed to be replicable, modular, and professional.

---

## The story behind this project

I started this project in March 2026. I didn't know how to code. I didn't know how to solder. I didn't know how to 3D print. I only had a problem to solve and the desire to learn.

Today, in August 2026, the system cools for 16 hours a day. The thermostats work. The manifold controls the valves. The logic for winter is ready. The system is already integrated with photovoltaics to optimize summer consumption.

It's not a finished product. It's an evolving project, built piece by piece, day by day. But it already has a professional footprint, and is designed to be replicable, structured, and complete.

---

## Why I built it

### The problem: short cycling

I have an underfloor heating system with an on/off heat pump. In winter, small zones (a bathroom, a small bedroom) require little water. The heat pump always runs at the same power: in two minutes it reaches the flow temperature and turns off. Then it turns on again after ten minutes. Dozens of cycles per day.

Wasted energy. Wear and tear. Inefficiency.

I wanted the pump to turn on only when it's really needed, and to stay on long enough to be efficient.

### Home automation must make sense

Most home automation is a waste of money. Lights that turn on by themselves, automated blinds, voice assistants: they're convenient, but they don't pay for themselves.

Heating and cooling are different. They account for sixty to seventy percent of the bill. Optimizing them delivers real economic returns.

### Commercial thermostats: expensive and closed

A branded WiFi thermostat costs from one hundred euros up to over two hundred and fifty. My thermostat costs less than fifteen euros in components.

But the problem isn't just cost. Commercial systems are often closed: they depend on proprietary clouds, don't integrate freely with Home Assistant, can't be modified or repaired. With DIY you get real customization: you can add features that didn't exist before, adapt the system to your needs, and have full control of your system.

### A solution that leverages ESP-NOW

ESP-NOW is a direct peer-to-peer communication protocol from Espressif. It allows ESP32 devices to communicate with each other without going through a WiFi router. In my system, thermostats talk to the manifold via ESP-NOW as primary or fallback channel. WiFi is used for communication with Home Assistant, but if WiFi goes down, the system continues to work.

Benefits: independence from the router, low latency, encrypted communication. And devices can act as repeaters to extend the network where the signal doesn't reach. A feature that many projects overlook, but which makes the system reliable and robust.

### Building is the real satisfaction

I could have bought commercial thermostats and a control system. But I wouldn't have learned anything. I wouldn't have had full control. I wouldn't have had the satisfaction of building something that didn't exist before.

Building is why this project exists.

---

**Built with passion, from scratch.**
