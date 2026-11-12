# Architecture

The core design rule of Janus Lab is: **Break must never reach Atlas, personal devices, or any management interface.**

To enforce this, the network is divided into zones, with a dedicated firewall managing the traffic between them. Remote access is handled exclusively through a private mesh VPN, meaning **zero ports are exposed to the internet**.

## Target Design

Three zones, one firewall, one port per zone.

*   **Home Zone:** The admin PC.
*   **Atlas Zone:** The stable server.
*   **Break Zone:** The vulnerable lab host, connected via a Lab Switch.

```mermaid
flowchart TD
    NET[Internet] --> MODEM["ISP Modem"]
    MODEM --> ROUTER["Lab Router<br/>gateway"]
    ROUTER --> FW["Zone firewall<br/>one port per zone"]
    FW --> HOME["Home zone<br/>admin PC"]
    FW --> ATLAS["Atlas zone<br/>stable server"]
    FW --> SW["Lab switch"]
    SW --> BREAK["Break zone<br/>vulnerable lab host"]
    REMOTE["Remote access<br/>private mesh VPN only"] -.-> ATLAS
```

No route exists from the Break zone to Atlas, the Home zone, or any management interface. Isolation is re-tested after every network change.