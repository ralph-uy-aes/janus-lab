# Hardware Inventory

This is the sanitized hardware inventory for Janus Lab. Specific model numbers and serials are omitted for privacy and security.

## Servers
*   **Atlas (Server A):** Custom-built desktop. Intel Core i5 (4th Gen), 16GB DDR3 RAM, 600W PSU. Role: Stable "everything" server (Proxmox, media, self-hosted services).
*   **Break (Server B):** Repurposed enterprise desktop. Intel Core i5, 16GB RAM, dedicated GPU (for future password-cracking practice). Role: Deliberately vulnerable security lab.

## Network
*   **ISP Modem:** Provided by ISP, bridging mode.
*   **Lab Router:** Wi-Fi 6E Tri-Band consumer router. Role: Primary gateway and household Wi-Fi.
*   **Zone Firewall:** Enterprise-grade firewall appliance (unpatched, no support subscription). Role: Enforces zone isolation between Home, Atlas, and Break.
*   **Lab Switch:** Repurposed enterprise firewall appliance (acting as a Layer 2 switch). Role: Break zone connectivity and a deliberate target.

## Storage
*   **Atlas Boot/VM:** 2x 256GB SSDs (mirrored).
*   **Atlas Data:** 2x 1TB HDDs (mirrored).
*   **Atlas Media:** 2TB USB External HDD.
*   **Break Storage:** 1x 256GB SSD (OS), 1x 1TB SSD (disposable VM data).
*   *Plus various spares and retired drives.*