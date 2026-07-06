Technical Runbook: VPN Client Unable to Connect from Home

Issue
VPN client fails to connect from a home network. Symptoms: VPN stuck at “connecting” stage. Suspected firewall (home router) blocking required port.

Root Cause Analysis
- Primary: Outbound UDP/TCP port 443 being blocked by the home router or ISP gateway, preventing the VPN handshake from completing.
- Secondary: VPN client attempting to bind to port 443 on the client-side host; firewall or NAT in the home network blocks outbound/inbound traffic for that port.
- Tertiary: If the VPN server requires a specific port, mismatched configuration may cause persistent connect failures.
- Observations: After changing VPN port to 1194, connectivity succeeds, indicating the home network allows 1194 (UDP) or the selected protocol is tolerated, while 443 is blocked.

Solution Overview
Change the VPN client connection port from 443 to 1194 (or an allowed alternative port) and validate router/firewall behavior. Verify client-side restart and network path, then re-test connectivity and establish a stable session.

Steps to Resolve
1) Prepare
- Confirm user scope: End-user has admin rights on VPN client and access to settings.
- Gather data: Current VPN client connection log, server port configuration, router model, and firewall rules.
- Back up current client profile/settings if possible.

2) Change Port in VPN Client
- Open VPN client application.
- Navigate to Settings or Preferences.
- Select Advanced settings.
- Locate Port configuration (initial value: 443).
- Change Port from 443 to 1194 (or other approved port, e.g., 1197, 500, depending on server configuration).
- Save/apply changes.

3) Restart and Reattempt Connection
- Important: Fully restart the VPN client after applying the port change.
  - Close the VPN client completely (exit to system tray, ensure no background processes).
  - Re-launch the VPN client.
- Initiate a new connection.
- Monitor the connection status and logs for success indicators (e.g., “Connected,” IP assigned, tunnel established).

4) Verify Network Path and Firewall
- Check client-side: Ensure no local firewall blocks the chosen port.
  - Windows: netsh advfirewall firewall show rule name=all | findstr /i "1194" (or your port)
  - macOS: sudo pfctl -sr | grep -i 1194 (if pf is in use)
- Check router/firewall:
  - Access router admin interface.
  - Review outbound/inbound firewall rules and port filtering.
  - Ensure UDP/TCP 1194 (as configured by VPN server) is allowed outbound.
  - If UPnP is enabled, ensure it does not override rules negatively.
- If possible, test on a different network (e.g., mobile hotspot) to verify if the issue is home-network-specific.

5) Validation
- Confirm VPN tunnel is established and route(s) are active:
  - Run ipconfig/ifconfig to verify VPN-assigned IP.
  - Run traceroute/tracert to VPN server to confirm path.
  - Check VPN server-side logs for accepted connection attempts.
- Validate throughput and stability for 5–10 minutes of continuous usage.

6) Documentation and Handoff
- Record: Successful port, server, and protocol details.
- Update runbook with router model and any specific port-forward or firewall rules configured.
- If issue persists on port 1194, coordinate with network team to audit VPN server port availability and potential ISP restrictions.

Common Mistakes to Avoid
- Not restarting the VPN client after changing settings.
- Leaving the router/firewall unchanged when port-blocking is suspected.
- Assuming port 443 will work without verification in the home environment.

Notes
- If the VPN server requires a specific port (e.g., 1194 UDP), ensure protocol alignment (UDP/TCP) with server configuration.
- In environments with strict NAT, consider enabling split-tunneling or using TLS/DTLS options if available.