**PLEASE** discuss any problems on the [Tunnelblick Discussion List](https://groups.google.com/forum/#!forum/tunnelblick-discuss).

The following are known problems or limitations in Tunnelblick:

  * iTunes 11.2 sometimes causes incorrect permissions to be set on /Users each time the computer is booted, leading Tunnelblick to refuse to launch because the folder is insecure. Update to iTunes 11.2.1 to resolve this problem.

  * The standard script that "Set nameserver" uses handles DNS for most common setups. For other situations, one of the other settings may work, or you can use custom scripts. See [Setting up Configurations](cConfigT#The_%22Set_Nameserver%22_Check_Box_and_DNS_&_WINS_Sett.md) for details.

  * When attempting to connect to a VPN using a TAP connection, OpenVPN may display a series of "write to TUN/TAP : Input/output error (code=5)" error messages. Although a few of these messages are normal, if they continue to be displayed for more than a few seconds, try to connect using "Set nameserver (alternate 1)".

  * When attempting to connect to a VPN, Tunnelblick may fail to load tun.kext or tap.kext. This can happen when another program, or another version of Tunnelblick, has loaded different versions of tun.kext and tap.kext. For example, the Cisco VPN client loads conflicting kexts at system startup, and they must be unloaded for Tunnelblick to work. Viscosity loads tun.kext and tap.kext when it is running. This problem may be avoided (for Viscosity) by quitting Viscosity, or (for Cisco) by using the [user-contributed script](DownloadsEntry#User-Contributed_Scripts.md) designed for that purpose.
> > If you are running on OS X 10.6.8 or higher and using OpenVPN 2.3.4 or higher and using a TUN device, the default Tunnelblick setting to "Load Tun Automatically" (on the "Advanced" settings window) will avoid this problem by not loading the tun kext -- OS X's built-in "utun" device will be used instead of a "tun" device.

  * Under some circumstances, traffic between two computers on a LAN may be routed through a bridged VPN. See [Issue 154 comment 10](http://code.google.com/p/tunnelblick/issues/detail?id=154#c10).

  * If "Set nameserver" is selected, all "up" and "down" options in the OpenVPN configuration file will be ignored. To work around this, include appropriate parts of the standard up/down scripts in your own scripts and select "Do not set nameserver". (The reason for this is that OpenVPN's "down-pre" option cannot be used with the standard "Set nameserver" down script, but may be used by custom scripts, so the two scripts cannot be used together.)

  * High values for the OpenVPN "verb" option may cause high (99+ %) CPU use by Tunnelblick. Reduce the "verb" value in the OpenVPN configuration file to 3 or 4 for best performance.

  * Beta versions do not include complete localization. If you can help localize Tunnelblick, please contact [project owner Jon](http://code.google.com/u/jkbullard/).


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###