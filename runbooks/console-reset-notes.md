# Console Reset Notes

These are the sanitized procedures used to factory-reset the enterprise network hardware for Janus Lab. 

*Note: Specific IP addresses, model numbers, and firmware versions are omitted from this public document. Always refer to the vendor's official documentation.*

## Zone Firewall

1. Power off the device.
2. Press and hold the recessed **Reset** button on the front panel.
3. While holding Reset, plug the power back in.
4. Continue holding until the "Attn" (Attention) LED flashes rapidly (approx 20-30 seconds).
5. Release the button and wait for the Attn LED to flash Red.
6. Perform a hard power cycle (hold power for 5 seconds, then turn back on).
7. Connect an Ethernet cable to the **Trusted (Eth1)** interface.
8. Access the Web UI using the default management IP. Default credentials are `admin` / `readwrite`.

## Lab Switch

1. Connect a USB-to-RJ45 console cable to the Console port.
2. Open a terminal at 9600 8-N-1.
3. Power on the device. 
4. Login with `admin` (leave password blank).
5. Run the CLI command: `execute factoryreset`
6. Confirm with `y`. The device will reboot.
7. Connect an Ethernet cable to **Internal Port 1**.
8. Access the Web UI using the default management IP. Default credentials are `admin` (blank password).