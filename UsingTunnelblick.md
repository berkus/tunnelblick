![http://tunnelblick.googlecode.com/files/tb-logo-613x127-2010-01-30.png](http://tunnelblick.googlecode.com/files/tb-logo-613x127-2010-01-30.png)

This document describes how to use Tunnelblick version 3.0.

**PLEASE** discuss any problems on the [Tunnelblick Discussion List](http://groups.google.com/group/tunnelblick-discuss).

This document contains the following sections:



## What is Tunnelblick? ##
  * **Explanation 1**: Tunnelblick is a program that can be used to securely connect a Mac running OS X to a remote network or the Internet, bypassing untrusted networks, censorship, and eavesdropping. It does this by creating a "Virtual Private Network", or "[VPN](http://en.wiktionary.org/wiki/Virtual_Private_Network) `[`wiktionary.org`]`", to a VPN server using a program named "OpenVPN", which is included within the Tunnelblick application. When you connect through a VPN, your computer sends all network traffic through a "tunnel" to the VPN server, which then passes on your network traffic to a local network or the Internet. It is as if you were connecting to the network or Internet through the VPN server instead of your computer. Usually, all traffic between your computer and the VPN server is encrypted.

> VPNs are primarily used two ways, or sometimes both ways simultaneously:
    * To securely connect a computer to the Internet, even though it may be connecting through an untrusted network (a wireless network at a hotel or airport, for example); and
    * To securely connect a computer to a company's internal network or some part of it (a branch office, for example).

> In addition to Tunnelblick, you need access to a VPN server. Your company may provide one, or you can obtain VPN service from any of several VPN service providers, or you can use another one of your computers or a router to act as a VPN server.

  * **Explanation 2**: Tunnelblick is a ready-to-use Graphic User Interface (GUI) for OpenVPN on Mac OS X. It provides easy-to-use control of OpenVPN server and/or client connections.

> It runs on OS X Tiger (10.4), Leopard (10.5), and Snow Leopard (10.6). It comes as a ready-to-use Universal application with all necessary binaries and drivers (including OpenVPN and tun/tap) included. No additional installation is necessary -- just add your configuration and encryption information.

> Tunnelblick is free software licensed under the GNU General Public License (GPL) Version 2.

For more information, including wikis and a discussion group, see the [Tunnelblick home page](http://code.google.com/p/tunnelblick/).

## Installing Tunnelblick ##
**Special note for those who may have installed RaptorVPN or Urban Shield VPN, VPN In China, or other VPN software**: These installations have backups that must be removed before installing or reinstalling Tunnelblick unless you are continuing to use the same service. See [this Discussion Group thread](https://groups.google.com/d/topic/tunnelblick-discuss/s368xGP5Qpk/discussion).

Note: there is no need to install OpenVPN separately - the Tunnelblick application contains both the Tunnelblick GUI and OpenVPN.

First, download the latest disk image from the featured downloads section on the [Tunnelblick project page](http://code.google.com/p/tunnelblick/). Double-click the downloaded .dmg file. An icon for a "Tunnelblick” disk will appear on the Desktop, and a window similar to the following will appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-dmg-2010-02-09.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-dmg-2010-02-09.png)

Double-click the Tunnelblick icon and a new window will appear, similar to the following:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-install-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-install-2010-02-06.png)

If you are reinstalling, upgrading, or downgrading Tunnelblick, the window will show the version number of the current copy and of the new copy. The current copy of Tunnelblick will be put in the Trash before it is replaced.

Click the "Install" button to copy Tunnelblick to your hard drive at the indicated location.

Once that is done (it may take a couple of seconds), a new window will appear, similar to the following:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-launch-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-launch-2010-02-06.png)

If you want to launch Tunnelblick now, click the "Launch" button.

If Tunnelblick is currently running, a window similar to the following will appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-running-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-running-2010-02-06.png)

Click the "Close VPN Connections and Stop Tunnelblick" to continue. After all connections are closed and Tunnelblick has quit, the new version of Tunnelblick will be launched. Continue with the following sections.

## The First Time Tunnelblick is Run on a Computer ##
The first time a new installation of Tunnelblick is run on a computer and after a reinstall, upgrade, or downgrade, it will display the following screen:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-password-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-password-2010-02-06.png)

Please enter the name and password of a computer administrator. Tunnelblick's imbedded OpenVPN needs root privileges because it needs to modify network settings by configuring new network devices, changing routes, and adding and removing nameservers. Because we don't want you to enter your administrator account name and password every time you start a VPN connection, Tunnelblick comes with a setuid root binary that allows it to start a VPN connection with super user rights. Tunnelblick uses your administrator account name and password so it can create this setuid root binary.

Continue on to the next section.

## The First Time Tunnelblick is Run by Each User ##
If this is the first time you have run Tunnelblick as a particular user, or the first time after some Tunnelblick upgrades, the following window will appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-check-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-check-2010-02-06.png)

Specify whether or not you wish to have Tunnelblick check for updates each time it is launched. Each time an update is available, you will be given a choice of whether to install the update or not.

When there are no configuration files in `~/Library/Application Support/Tunnelblick/Configurations` (which is usually the case the first time Tunnelblick is run by each user when using a non-deployed version of Tunnelblick), the following window will appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-welcome-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-welcome-2010-02-06.png)

If you click "Install and edit sample configuration file”, Tunnelblick will create a sample OpenVPN configuration file at `~/Library/Application Support/Tunnelblick/Configurations/openvpn.conf`, then open it in TextEdit for you to modify.

If you click "Quit”, Tunnelblick will quit without doing anything.

If you click "Open configuration folder", Tunnelblick will open a Finder window with `~/Library/Application Support/Tunnelblick/Configurations`, and then quit. Move or copy your OpenVPN configuration file(s) -- files with extensions of ".oven" or ".conf" -- to this window. If you have received key files or certificate files with your configuration file, move or copy them to this window also.

To launch Tunnelblick after setting up configuration and other files, double-click "Launch Tunnelblick" in the `Configurations` folder, or double-click Tunnelblick in the Applications folder.

## Normal Tunnelblick Operation ##
Once Tunnelblick has been launched, you control it from the icon in the Status Bar at the top of your screen. The Tunnelblick icon is usually placed between the time and the Spotlight icon. When no VPN connection is active, the icon is dark, indicating a closed tunnel:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-closed-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-closed-2010-02-04.png)

If you click on the icon, you'll see a drop down menu similar to the following:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-menu-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-menu-2010-02-06.png)

There will be a "Connect” menu item for each .ovpn or .conf file in `~/Library/Application Support/Tunnelblick/Configurations`. Click on one to establish the corresponding pre-configured VPN connection. To illustrate the connection being established, three dots will appear in the menu item, and the Tunnelblick icon will darken and lighten repeatedly. If the connection is successfully opened, the icon will change to show an open tunnel:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png)

Depending on your setup, you may be asked for a passphrase or username/password combination. You can save your passphrase or password in Apple's Keychain by checking the appropriate checkbox.

The connection will be active as long as you do not end it or log out. Putting your computer to sleep will close the connection but upon waking up from sleep Tunnelblick will attempt to reestablish the connection. If Tunnelblick loses contact with the server (because of a lack of wireless signal, for example), it will periodically try to re-establish the connection.

If a connection error occurs, or in the unlikely event of an interface crash, Tunnelblick will terminate the VPN tunnel and record the error in the Console Log.

Use "Disconnect” from the drop-down menu to close the VPN connection. Use "Quit” to close all open connections and quit the program and prevent Tunnelblick from starting itself at your next login at your computer.

If Tunnelblick is running when you logout (or your computer crashes, or is shut down or restarted), then Tunnelblick will be started automatically upon login. To stop Tunnelblick from being started automatically upon login, be sure to quit Tunnelblick before logging out, either by using the "Quit” command, or by using Command-Q (Apple-Q) when the "OpenVPN Log” or "About…” window is active. (Don't confuse this automatic launch of Tunnelblick upon login with the "automatically connect on launch” option, which causes a connection to be established when Tunnelblick is started.)

## The "Options…" Submenu ##
When the Tunnelblick menu is displayed, if you hover over "Options", the Options Submenu appears:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-options-menu-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-options-menu-2010-02-06.png)

Click on an item in the Options Submenu to change a preference, check for updates, or display the "About" window. For more details on preferences, see [Preferences](Preferences.md).

Some deployed versions of Tunnelblick do not display the Options Submenu (it is controlled by a preference), in which case the "Options" menu item is replaced by "About Tunnelblick..."

## The "Details…" ##
When the Tunnelblick menu is displayed, if you click on "Details…” a window similar to the following will appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-details-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-details-2010-02-04.png)

There will be a tab for each connection (i.e., each .ovpn or .conf file), whether the connection is open or closed. Each tab contains a pane with the OpenVPN Log for the connection and checkboxes that provide options for that connection:

  * "automatically connect on launch” causes the connection to be opened when Tunnelblick is launched (started). "automatically connect on launch” is unchecked by default.

  * "Set nameserver” causes scripts to be run before a connection is opened and after the connection is closed. The scripts save and restore DHCP DNS and WINS information. "Set nameserver” is checked by default.

> When a connection is attempted, the script for "Set nameserver” saves the current DNS settings and removes DNS settings that were set by DHCP (manual DNS settings are _not_ removed). When a connection is disconnected the scripts restore the saved DNS settings. The scripts do not support the simultaneous use of two or more nameservers for different domains; custom up/down scripts must be used for this purpose.

  * "Monitor connection" causes the network connection to be monitored for changes. It is available only when "Set nameserver" is checked. When a change is detected, the connection will be disconnected and reconnected. "Monitor connection" is checked by default, but the connection is only monitored when "Set nameserver" is checked.

In addition, the "OpenVPN Log” window contains four buttons:

  * "Clear log” clears the OpenVPN Log for the connection being displayed.

  * "Edit configuration” starts TextEdit with the configuration file containing the OpenVPN configuration for the connection being displayed so it can be edited. If you modify a configuration file, you will need the username and password of a computer administrator to connect using the modified configuration file.

  * "Connect” opens the connection being displayed.

  * "Disconnect” closes the connection being displayed.

You may use the standard keyboard shortcuts in the "Details…" window: Command-C, Command-X, and Command-V for copy, cut, and paste; and Command-A, Command-M, Command-W, and Command-Q to select all the text in the log that is currently being displayed, minimize the window to the dock, close the window, and quit the program.

## The "About…" Window ##
Click on the Tunnelblick icon in the Status Bar at the top of your screen between the time and the Spotlight icon, then (if it is visible) click on "Options", then on "About…” to open a window with information about the versions of Tunnelblick and OpenVPN that are running and a link to the Tunnelblick website.

## The "Set Nameserver" Check Box and DNS & WINS Settings ##
If you are using DHCP, wish to use DNS and WINS servers at the far end of the tunnel when connected, and the VPN server you are connecting to "pushes" DNS and WINS settings to your client, put a check in the "Set nameserver" checkbox. (This is the situation for most users.)

If you are using DHCP, wish to use your original DNS and WINS servers when connected, and the VPN server you are connecting to does not "push" DNS or WINS settings to your client, un-check the "Set nameserver" checkbox.

If you are using manual settings, different versions of OS X behave differently. This is due to a change in network behavior in Snow Leopard and is beyond the scope of this project to fix.

If you're using Leopard (10.5) or Tiger (10.4), then it is possible to use the VPN-server-supplied DNS and WINS settings **in addition to** your manual settings by checking the "Set nameserver" box. However, your manual settings will always take precedence over any VPN server-supplied settings.  If "Set nameserver" is un-checked, you will continue to use only your manually-configured settings and any VPN server-supplied settings will be ignored.

If you are using Snow Leopard (10.6), then your manually-configured DNS and WINS settings will **always** be used, and no aggregation of configurations will be performed.

  * If you set your DNS servers manually, then regardless of the state of the "Set nameserver" box, your manual DNS servers will always be the only ones used.

  * If you set your Search Domain(s) manually, then regardless of the state of the "Set nameserver" box, your manual Search Domains will always be the only ones used.

  * If you set your WINS servers manually, then regardless of the state of the "Set nameserver" box, your manual WINS servers will always be the only ones used.

  * Each of these settings is independent of the others: if "Set nameserver" is checked, those settings not configured manually will be replaced by the settings obtained from the VPN server.  If "Set nameserver" is not checked, then as with Leopard/Tiger, no DNS/WINS settings will be applied.

**If your situation is not described above** (e.g., if you use manual DNS settings and wish to use DNS servers at the far end of a tunnel when connected, or you wish to use the OS X ability to use different nameservers for different domains), you must create your own up/down scripts and un-check the "Set nameserver" checkbox.

## THE "MONITOR CONNECTION" CHECKBOX ##
If checked (the default), the "Monitor connection" checkbox instructs Tunnelblick to monitor the connection's interface for changes. If Tunnelblick detects a change to DNS or WINS, the connection will be restarted. Under certain circumstances, repeated and unnecessary restarts are peformed; unchecking this box stops this from occurring.

Note that connection monitoring is not available unless "Set nameserver" is checked.

## Using More than One VPN Connection ##
You can put more than one .ovpn or .conf file together with its key and/or certificate files into the ~/Library/Application Support/Tunnelblick/Configurations folder. Tunnelblick interprets each .ovpn or .conf file in the ~/Library/Application Support/Tunnelblick/Configurations folder as a configuration file for a different connection; each of the connections will be available in the drop down menu and shown as a separate tab in the "OpenVPN Log” window.

## Using More than One VPN Connection Simultaneously ##
Tunnelblick can maintain multiple simultaneous open connections to different VPNs.

However, this is for experts only:

  * If you use "Set nameserver” (which uses standard scripts to save/change/restore DNS resolution data), on one or more connections your DNS settings may not be saved and restored properly and DNS might or might not work. It depends on the order in what DNS settings you want to use and which connections are opened and closed. Connections may close and be reopened because of communications errors over which you have no control, which can cause unpredictable results. Not recommended.
  * If you don't use "Set nameserver”, and your customized configuration files are suitably written to work together with custom scripts, things can work. But if you don't handle the DNS and routing settings properly, lots of things could go wrong. So this isn't recommended either unless you really know what you're doing and have a NEED to connect to multiple VPNs simultaneously.
  * VPN administrators might not be happy that you are connecting their networks together. Most VPN client software limits you to a single connection, probably for that reason.

## Automatically Starting Tunnelblick Upon Login ##
Tunnelblick was designed as a persistent menu icon that survives reboots. To this end, it inserts itself into the login items when it is started and only removes itself from the login items when you choose Quit from the menu or Command-Q from the "OpenVPN Log” window or "About..." window. . So if you just log out, shut down, or restart your computer, or it crashes, the next time you log in, Tunnelblick will automatically start. If you do not want Tunnelblick to start automatically, quit Tunnelblick before you log out, shut down, or restart.

## Automatically Opening a VPN Connection When Tunnelblick Starts ##
You can specify that a connection automatically be opened when Tunnelblick starts by putting a check in the "automatically connect on launch” checkbox for that connection. The checkbox is located on the connection's tab in the "OpenVPN Log” window.

## Using openvpn-down-root.so ##
When using "Set nameserver", it is usually necessary to avoid using the OpenVPN "user" and "group" options. These options cause OpenVPN to drop root privileges and take the privileges of the specified user and group. It this is done, then the standard scripts that handle restarting connections when there is a transient failure fail, because they are run without root privileges. And restoring routes when a tunnel is disconnected fails, too. So the "user" and "group" OpenVPN options should not be specified.

However, starting with Tunnelblick version 3.0b22, Tunnelblick includes the "openvpn-down-root.so" plugin for OpenVPN. It is located in theTunnelblick.app/Contents/Resources" folder. This plugin, when activated by including a line in the configuration file, allows the use of the "user" and "group" options, so that OpenVPN drops root privileges, but still has the scripts run as root, so reconnecting after transient network problems, or restoring routes when a tunnel is disconnected continue to work.

To activate the plugin:
  1. Set the per-configuration boolean preference "CONFIG\_NAME-useDownRootPlugin" to true.  If your configuration file is named "xyz.conf", the preference key is "xyz-useDownRootPlugin". (To set up the preference, use "Property List Editor.app" to  edit ~/Library/Preferences/com.openvpn.tunnelblick.plist and add the key, then right-click it and change the type to "boolean" and check it. “Property List Editor.app” is a small part of the free [Developer Tools](http://developer.apple.com/technology/Xcode.html) available from Apple (a free Apple Developer Connection membership is required). The Developer Tools are a very large (over 900MB download) suite of programs for developing software for Macs.)
  1. Include the following line in your configuration file:
```
    plugin path-to-openvpn-down-root.so     path-to-client.down.osx.sh
```
Example: If Tunnelblick.app is located in /Applications, the line would be:
```
    plugin /Applications/Tunnelblick.app/Contents/Resources/openvpn-down-root.so    /Applications/Tunnelblick.app/Contents/Resources/client.down.osx.sh 
```
Example: If Tunnelblick.app is located in /Applications and you have "Set nameserver" checked but "Monitor connection" unchecked, the line would be:
```
    plugin /Applications/Tunnelblick.app/Contents/Resources/openvpn-down-root.so    /Applications/Tunnelblick.app/Contents/Resources/client.nomonitor.down.osx.sh 
```
Example: If using a "deployed" version of Tunnelblick:
```
    plugin ../openvpn-down-root.so    ../client.down.osx.sh
```
## Preferences ##
See [Preferences](Preferences.md).

## Uninstalling Tunnelblick ##
See [Uninstalling Tunnelblick](cInstall#Uninstalling_Tunnelblick.md)

## Configuration Files ##
Each tunnel to be opened by Tunnelblick needs an OpenVPN configuration file. Tunnelblick considers any file located in ~/Library/Application Support/Tunnelblick/Configurations with an extension of .conf or .ovpn to be a configuration file, and presents each such file as a potential "connection”. (The "~" refers to your home folder.) Often these configuration files will be supplied to you. Refer to [the OpenVPN documentation](http://openvpn.net/index.php/open-source/documentation/manuals/69-openvpn-21.html) for details about what the configuration file should contain. (Note that some OpenVPN options are available only on Windows.)

When using a "deployed" version of Tunnelblick, configuration files are all located within the Tunnelblick application itself, so ~/Library/Application Support/Tunnelblick/Configurations is not used for configuration files (although it may be used for keys, certificates, and/or shell scripts). See [Deploying Tunnelblick](cDeployingTunnelblick.md) for details.

Tunnelblick monitors the folder that contains the configuration files. If a configuration file is added, the new configuration is available immediately without restarting Tunnelblick or disturbing existing connections. If a  configuration is removed from the folder, any connection using that configuration is immediately disconnected. To disable this behavior, use "doNotMonitorConfigurationFolder". (See [Preferences](Preferences.md).)

The configuration file may also be "shadow" copied to the /Library/Application Support Tunnelblick/Users/_username_ folder. This is done transparently for configuration files located on network volumes. The user should never manipulate this folder or its contents directly; Tunnelblick will do so automatically. (See "useShadowConfigurationFiles" in [Preferences](Preferences.md).)

If Tunnelblick's "Set nameserver” option is used:
  * Any "up” or "down” options in the configuration file will be ignored.
  * If any "user” or "group” options appear in the configuration file, DNS settings will not be restored when a tunnel is disconnected.

## File Locations ##
Tunnelblick preferences are contained in ~/Library/Preferences/com.openvpn.tunnelblick.plist. (The "~” indicates your home folder.) Deployed versions of Tunnelblick may contain a "forced-preferences.plist" file within the Tunnelblick application itself; see [Deploying Tunnelblick](cDeployingTunnelblick.md) for details.

OpenVPN configuration files are stored in ~/Library/Application Support/Tunnelblick/Configurations. Usually the key and certificate files are stored there, too. Since these files are all located in the user's Library folder, they must be set up separately for each user.

Note 1: Prior to Tunnelblick version 3.0b24, configuration files were stored in ~/Library/openvpn. Version 3.0b24 and later versions automatically move that folder to its new location, and replace it with a symbolic link to the new location.

Note 2: _Deployed_ versions of Tunnelblick contain the configuration file(s), so they do not need to be set up for each user -- any user that can access Tunnelblick.app can connect to VPN.

"Shadow" copies of configuration files (if they exist) are located in /Library/Application Support Tunnelblick/Users/_username_. (See "useShadowConfigurationFiles" in [Preferences](Preferences.md).)

See [Deploying Tunnelblick](cDeployingTunnelblick.md) for details of file locations when using a deployed version of Tunnelblick.

Within the Tunnelblick.app application, client up/down scripts and openvpn-down-root.so are located in Tunnelblick.app/Contents/Resources (see the "Set nameserver” checkbox in the "Details… window” section). To access Tunnelblick.app/Contents in the Finder, control-click Tunnelblick.app in the Applications folder, then click on "Show Package Contents”.

## When a Configuration File Changes ##
Whenever a configuration file changes, you will need to enter the name and password of a computer administrator. This is done as a security measure: because configuration files can contain references to scripts that run as root, they are owned by root and an administrator must grant permission to use them.

## COMMAND-LINE INTERFACE ##
Tunnelblick also contains openvpnstart, an OS X command line interface to OpenVPN which provides a scriptable way to create and destroy OpenVPN tunnels. openvpnstart is located in Tunnelblick.app/Contents/Resources. For details on using openvpnstart, run it from a Terminal window with no arguments.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###