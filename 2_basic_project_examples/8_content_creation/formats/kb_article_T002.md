Title: VPN Connection Won’t Connect from Home — Step-by-Step Help

Overview
If your VPN client won’t connect from home, you’re not alone. Sometimes a firewall (FW) on your router or home network blocks the VPN’s normal connection. A quick change to the port used by the VPN can fix this. This guide walks you through a simple, step-by-step process to get you back online.

What happened
- The VPN was stuck on connecting.
- It looked like the firewall on the home router blocked the usual port (443).
- We switched the VPN to a different port (1194), and it started working.
- If it still doesn’t connect, you may need to check your router’s firewall settings.

What you’ll need
- Your computer or device connected to your home network
- Access to your VPN client (the program you use to connect)
- Access to your home router’s admin interface (usually via a web browser)
- Your VPN login information (username, password, or certificate, if required)

Step-by-step fix: Change the VPN port to 1194
1) Open the VPN client
- Launch the VPN app you normally use.
- If you’re prompted to choose a profile or server, you can continue with the default setup.

2) Go to Settings
- In the VPN client, look for a menu called Settings, Preferences, or Tools.
- Open that menu to find more options.

3) Find the Advanced settings
- Look for an option labeled Advanced, Network, or Connections.
- Open Advanced settings to see port options.

4) Change the port from 443 to 1194
- In the Port field, delete 443 and enter 1194.
- If you see separate fields for TCP/UDP, the default is usually UDP; you can leave it as UDP unless your setup specifies otherwise.
- Save or Apply the changes.

5) Reconnect the VPN
- Go back to the main screen of the VPN client.
- Click Connect.
- If prompted, re-enter your login information or reselect your profile.

6) Verify the connection
- Once connected, you should see a status message or a key icon in the taskbar/system tray.
- You can try loading a website or using a resource you normally access through the VPN to confirm it’s working.

If it still fails, check your home router firewall
1) Access your router’s admin page
- Open a web browser and enter the router’s IP address (common ones: 192.168.0.1 or 192.168.1.1). If you’re unsure, check the label on the router or your internet service provider’s instructions.
- Log in with your admin username and password.

2) Locate firewall or security settings
- Look for sections named Firewall, Security, Access Control, or Port Filtering.

3) Check port blocking
- See if port 443 is blocked or restricted for outbound traffic.
- If you can, temporarily allow or open port 443 as a test. You can also search for “VPN port 1194” in your router settings and ensure outbound connections on UDP 1194 are allowed.

4) Save and test again
- Save any changes, reboot the router if required, and try the VPN again.

If you still have trouble
- Double-check your VPN profile: ensure you’re using the correct server/endpoint and authentication method.
- Confirm your device’s firewall or security software isn’t blocking the VPN.
- Reach out to your IT helpdesk or VPN provider for the exact port and protocol settings for your setup.

Helpful tips
- Port 1194 is commonly used for OpenVPN with UDP; using this port can help when port 443 is blocked.
- Make a note of your original port (443) in case you need to revert.
- Changes to router settings can affect other devices—only adjust settings you’re comfortable with, or ask for help.

You’re doing great. If you’d like, I can tailor these steps to your specific VPN client or router model.