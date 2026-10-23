# janus-lab
🌏 Atlas + ☄️ Break Blog

An educational home lab: two physical servers behind one firewall, kept strictly separate.
**Atlas** runs everyday self-hosted services; **Break** is deliberately made vulnerable and
rebuilt, to practice detection engineering (blue team) and attack (red team).

> Educational home lab. Configurations are sanitized: no real addresses, hostnames, serial numbers, or credentials appear in this repository.

## Architecture

```mermaid
flowchart TD
    NET[Internet] --> GW["ISP modem/router"]
    GW --> FW["Zone firewall<br/>one port per zone"]
    FW --> HOME["Home zone: admin PC"]
    FW --> ATLAS["Atlas zone: server"]
    FW --> SW["Lab switch"]
    SW --> BREAK["Break zone: lab host"]