## Printer shows offline even though it’s powered on

Experiencing an offline printer can be frustrating, especially when the device appears to be powered on and ready but nothing prints. This guide helps you resolve common causes, including an IP address conflict and connection issues, so you can get back to printing quickly.

Problem statement
Your printer is listed as offline in your computer or network, even though the printer’s power indicator is on. The root cause is often a network address (Internet Protocol) conflict or a stalled print service rather than a hardware failure.

Step-by-step instructions

1) Check the printer’s network address
- Verify the printer’s current Internet Protocol address on its control panel or network status page.
- If you see an address that conflicts with another device on the network, you need to release that address and obtain a new one via Dynamic Host Configuration Protocol (DHCP).

2) Release and renew the IP address (DHCP)
- Access the printer’s settings menu and choose the option to release the current IP address, if available.
- Select renew or obtain a new IP address automatically. If your printer supports this, it will request a new IP from the DHCP server.
- If your printer does not have an on-device option, you can release/renew the IP from your computer or router:
  - On a Windows computer: open Command Prompt as Administrator and type:
    - ipconfig /release then Enter
    - ipconfig /renew then Enter
  - On a Mac: open Terminal and type:
    - sudo ipconfig set en0 DHCP (replace en0 with the correct network interface)
- [Screenshot: Printer network settings showing IP address] 

3) Restart the print spooler service
- The print spooler manages print jobs on your computer. Restarting it can clear stuck jobs and re-establish communication.
- Windows:
  - Open Services (search for “Services”), find Print Spooler, and click Restart.
  - If you prefer the command line: net stop spooler followed by net start spooler.
- macOS:
  - Open Activity Monitor, find the printjob process, and quit it. The system will automatically restart the service when needed.
- [Screenshot: Services window with Print Spooler highlighted]

4) Re-add the printer if needed
- Remove the printer from your computer’s list, then add it again using the correct network address.
- Windows:
  - Settings > Bluetooth & devices > Printers & scanners > select the printer > Remove.
  - Add a printer or scanner and follow the prompts to add it back by network IP.
- macOS:
  - System Settings > Printers & Scanners > select the printer > minus button to remove.
  - Add printer again using the IP address (IPP or AirPrint) as appropriate.
- Ensure you select the correct printer driver when re-adding. Incorrect drivers are a common cause of continued “offline” status.
- [Screenshot: Add printer dialog with IP address field]

Troubleshooting section

- Common cause: IP address conflict
  - Ensure the printer is set to obtain an IP address automatically (DHCP) or assign a unique static IP outside the DHCP pool.
- Common cause: Wrong printer driver
  - Install and select the correct driver for your printer model and operating system.
- Common cause: Spooler not running
  - Always restart the Print Spooler after any networking changes or if print jobs hang.
- Common cause: Physical network issues
  - Verify Ethernet cables are securely connected or confirm Wi‑Fi signal strength if the printer is wireless.
- [Screenshot: Network diagram showing DHCP server, printer, and computer]

Warnings about common mistakes
- Do not ignore IP address conflicts; assigning the same IP to multiple devices causes continued offline status.
- Do not recycle old drivers; using an outdated or incorrect driver can prevent printing.
- Do not assume the problem is the printer hardware; network or service issues are frequent culprits.

Still need help?
If you’ve tried these steps and the printer remains offline, contact your IT support or the printer manufacturer’s help desk. Provide details such as:
- Printer model and current IP address
- Steps you took (DHCP release/renew, spooler restart, re-adding the printer)
- Any error messages displayed on the printer or computer
We’re here to help and can guide you through more advanced network checks if required.