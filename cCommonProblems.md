
### It's complicated! ###
OpenVPN is such a powerful tool with so many options, and computer configurations are so varied, that it is impossible to have an exhaustive troubleshooting guide. This guide is meant for the most common setups, so if it doesn't apply to your situation, or doesn't help, ask the [Tunnelblick Discussion Group](https://groups.google.com/forum/#!forum/tunnelblick-discuss) or the [OpenVPN users mailing list](http://news.gmane.org/gmane.network.openvpn.user) for help.

## I used a different program and uninstalled it, but with Tunnelblick all I can see are my old configurations! ##
The different program (for example, Urban Shield) uses a customized version of Tunnelblick that makes backups of their configurations and restores them when Tunnelblick starts up, and also hides all other configurations. To solve this problem:
  1. Rename the /Library/Application Support/Tunnelblick folder to be named Tunnelblick.old. (This will hide the backup, so Tunnelblick doesn't see it and doesn't restore it.)
  1. Reinstall Tunnelblick from the .dmg (disk image)

## How can you tell if OpenVPN connected to the server properly? ##
  1. Click on the Tunnelblick icon at the top of the display.
  1. See what appears in the drop-down list for the configuration you are trying to troubleshoot:
    * If the entry shows **Connect xyz**, configuration xyz is **not connected** and Tunnelblick is not trying to connect
    * If the entry shows **√ Disconnect xyz**, configuration xyz **is connected**
    * If the entry shows **- Connect xyz**, Tunnelblick is **trying to connect** configuration xyz

## If OpenVPN is not connected to the server ##
If OpenVPN can't connect to the server, there should be one or more error messages in the OpenVPN log to indicate what the problem is. To see the OpenVPN log, click on the Tunnelblick icon, click on "VPN Details…", then click on the name of the configuration you are troubleshooting. The OpenVPN log is the large area of black text on a white background. (It contains messages from Tunnelblick in addition to the messages from OpenVPN.)

Look at lines near the end of the log for an error message.


## OpenVPN Connects, but you can't surf the Internet ##
See [Connects OK, But...](cConnectedBut.md).


## A connection is established, but drops out or is restarted after a few minutes, or DNS stops working after a few minutes ##
This can have several causes:
  * Another computer on your network is attempting to connect to the VPN using the same credentials.
  * You have a version of Tunnelblick earlier than 3.1beta04 and have both "Set nameserver" and "Monitor connection" checked. When DHCP is renewed, the changes can cause earlier versions of Tunnelblick to restart the connection. Update to the latest version of Tunnelblick.
  * You have "Monitor connection" UNchecked. When DHCP is renewed, the change is ignored (because "Monitor connection" isn't checked) and the VPN-supplied DNS server is replaced with the DHCP-supplied server. Often a DHCP-supplied server will only respond to queries which originate within that network. Since the DNS queries originate from the VPN, which is outside of that network, the queries will not be answered. Update to the latest version of Tunnelblick and put a check next to "Monitor network".


## An error messages says to see details in the Console Log ##
See [The Console Log](cConsoleLog.md) for instructions on viewing the Console Log.


## An error message says "write to TUN/TAP : Input/output error (code=5)" ##
OpenVPN may display a series of these messages when using a TAP connection. Although a few such messages are normal, if they continue to be displayed for more than a few seconds and the connection is never established, try to connect using "Set nameserver (alternate 1)" in Tunnelblick 3.2beta10 or later.


## An error message says "Tunnelblick could not be launched because of a problem with the configuration. Please examine the Console Log for details." ##
This is usually caused by a problem with the private configuration folder. (Tunnelblick sets this up, but if you accidentally delete a critical file or folder, this could happen.) The Console log will contain details about the specific problem. See [File Locations](cFileLocations.md) for information about how the files and folders should be set up.

(See [The Console Log](cConsoleLog.md) for instructions on viewing the Console Log.)

## An error message says "You have tried to connect using a configuration file that is the same as the sample configuration file installed by Tunnelblick" ##
This means that you have tried to connect to a VPN without setting up a configuration file. Consult your network administrator or your VPN service provider to obtain configuration and other files or the information you need to modify the sample file. For more information, see [Getting VPN Service](cGettingVPNService.md).


## An OpenVPN log entry says "potential route subnet conflict" ##
This means that the remote network you are creating a VPN to has IP addresses that are also in your local LAN.

The easiest way to fix this is usually to change the addresses of your local LAN. You do this by changing your router's configuration. For some routers you specify the first three numbers of the LAN (e.g. 192.168.77); in other routers you specify the address of the router itself (e.g. 192.168.77.1).

After changing the LAN address, you should restart all computers (and other network devices including network printers), so they start using addresses in the new address range.

Example:
> `WARNING: potential route subnet conflict between local LAN [192.168.1.0/255.255.255.0] and remote VPN [192.168.1.0/255.255.255.0]`

This means that both the remote network and your local network are using the 192.168.1.`*` range of IP addresses. So change your local network to use, for example, 192.168.5.`*`, or 192.168.23.`*`. If you get the same warning message, try another address range.


## An OpenVPN log entry says "Message hash algorithm 'SHA512' not found (OpenSSL)" ##
Update to Tunnelblick 3.1beta14 or later.


## An OpenVPN log entry says "Cannot allocate TUN/TAP dev dynamically" ##
This problem indicates a problem with the tun/tap kexts.
  * It could be caused (prior to Tunnelblick version 3.0b22),  by trying to make a connection while running the Snow Leopard kernel in 64 bit mode. Update to the latest version to correct this problem.
  * It can be caused by the following sequence in the configuration file:
> > dev-type tun<br>
<blockquote>dev abcdefg<br>
</blockquote></li></ul><blockquote>and a workaround is to change to the single line
> > dev tun

> (or substitute "tap" for "tun" in the above if you are using the tap interface.)
  * It can be caused by extra "tun" or "tap" kexts being loaded. See the following entry.


## An OpenVPN log entry says "Tunnelblick: openvpnstart status #247: Error: Unable to load tun and tap kexts. Status = 71" ##
See the following entry.
## An OpenVPN log entry says "Tunnelblick: openvpnstart status #247: Error: Unable to load net.tunnelblick.tun and/or net.tunnelblick.tap kexts in 5 tries. Status = 71" ##
This means that Tunnelblick was unable to load the tun and/or tap kexts (device drivers) it needs to make a VPN connection. Usually that is because there are incompatible kexts already loaded. Recent versions of Tunnelblick try to be "good citizens" by loading kexts only when needed, and unloading them when they are no longer needed. However, some other VPN clients (Cisco AnyConnect SSL VPN, for example) load their own, incompatible kexts when the computer is started and leave them loaded, whether or not a VPN connection is in use. (Some non-VPN software also loads incompatible kexts -- for example, Pogoplug loads a "com.pogoplug.xcetun" tun kext which interferes with Tunnelblick's tun kext.)

To find out if this is what is causing the problem, use the "kextstat" command in a Terminal window. It will list all of the loaded kexts. Usually the tun and/or tap kexts show up at or near the end of the list. Common tun/taps are:
  * net.tunnelblick.tun and net.tunnelblick.tap: These are the kexts used by current versions of Tunnelblick. The appropriate one (tun or tap) is loaded when a connection is requested, and unloaded when it is disconnected.
  * foo.tun and foo.tap: These are kexts for obsolete Cisco and Tunnelblick VPN clients (and some others), loaded when an older version of Tunnelblick is launched (and unloaded when the computer restarts). If Tunnelblick detects them, it will offer to unload them before connecting.
  * com.cisco.cscotun: This is Cisco AnyConnect SSL VPN kext. Cisco's installer causes it to be loaded when the computer starts.
  * com.viscosityvpn.Viscosity.tun and com.viscosityvpn.Viscosity.tap: These are kexts used by the Viscosity VPN client.
  * com.pogoplug.xcetun: This kext is associated with Pogoplug.
  * anchorfree.tun: This kext is associated with HotSpot Shield VPN.
But any non-Apple kext with "tun" or "tap" in its name is likely to be causing the problem.

To unload kexts and allow Tunnelblick to load its own kexts, use the 'kextunload" Terminal command to unload each loaded tun and tap kext individually. For example, to unload com.viscosityvpn.Viscosity.tun, type the following:

> `sudo kextunload -b com.viscosityvpn.Viscosity.tun`

(The "sudo" is necessary because this command modifies the device driver. You will be asked for your administrator password, which will not appear (even as asterisks) when you type it.)

If you find that restarting your computer reloads the kext you might need to find where it is being loaded from. Common locations are
  * /Users/_your username_/Library/LaunchDaemons
  * /Users/_your username_/Library/LaunchAgents
  * /Library/LaunchDaemons
  * /Library/LaunchAgents
  * /System/Library/LaunchDaemons
  * /System/Library/LaunchAgents

There are a user-contributed scripts on the <a href='http://code.google.com/p/tunnelblick/wiki/DownloadsEntry?tm=2'>Downloads</a> page that will automatically unload the Cisco kext when Tunnelblick makes a connection, and reload the Cisco kext when the connection is disconnected.

## An OpenVPN log entry says "Cannot load certificate file XXX.crt: error: 02001002:system library:fopen:No such file or directory: error: 20074002:BIO routines:FILE\_CTRL:system lib: error:140AD002:SSL routines:SSL\_CTX\_use\_certificate\_file:system lib " ##
Your certificate file (XXX.crt) was not found. Usually the file should be in the same folder as the configuration file, ~/Library/Tunnelblick/Configurations, not in a subfolder. For example, if the configuration file has a line such as
> cert abcde.crt
or
> ca abcde.crt
then the file abcde.crt should be in the same folder as the configuration. If the configuration file has a line such as
> cert xyz/abcde.crt
or
> ca xyz/abcde.crt
then the file abcde.crt should be in the xyz subfolder of the folder with the configuration.

## An OpenVPN log entry says "TLS Error: Auth Username/Password was not provided by peer" ##
Your client configuration file should include an "auth-user-pass" option.

## An OpenVPN log entry says "script failed: could not execute external program" ##
An up or down script contains an error. Common causes:
  * The use of a script file with Windows line breaks (CR-LF) instead of Unix/Mac line breaks (LF).
  * The use of a script file that does not have execute permission for root.
  * The use of a script file with syntax errors.

## Various problems when waking from computer sleep ##
There are several problems that can occur when the computer wakes from sleep. One solution to most problems is to set the configuration to "Disconnect when the computer goes to sleep" but NOT "Reconnect when the computer wakes from sleep", and reconnect manually when you wake up the computer. If that doesn't work, you may have to manually disconnect the VPN before putting the computer to sleep and then manually reconnect it when the computer wakes up. This problem is being worked on and should be fixed "soon" (maybe sometime in July or August 2014).


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###