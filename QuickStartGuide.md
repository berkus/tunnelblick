**PLEASE** discuss any problems on the [Tunnelblick Discussion List](http://groups.google.com/group/tunnelblick-discuss).

Take a look at [What Tunnelblick Is](QuickStartGuide#What_Tunnelblick_Is.md) if you aren't sure.

This is a **Quick Start Guide** to Tunnelblick; for a more through and complete discussion of Tunnelblick see [Using Tunnelblick](UsingTunnelblick.md).

This document contains the following sections:



## Installing Tunnelblick and Getting it Set Up ##
Here is what you need to get started using Tunnelblick:
  * The username and password of an administrator for your computer.
  * A copy of the Tunnelblick installation disk image. You can download one from the [Tunnelblick project home page](http://code.google.com/p/tunnelblick).
  * An OpenVPN configuration file or information about your VPN configuration. You get that from whoever set up your VPN (usually your company or VPN service provider).
  * Key and certificate files for encryption and authentication. Again, get them from whoever set up your VPN.

To get started, double-click the disk image.

A window will open. Double-click the Tunnelblick icon in the window to start the installation process.

You will be asked if you want to install/reinstall/upgrade/downgrade Tunnelblick. Click the "Install" button to install Tunnelblick to your Applications folder. If you are reinstalling, upgrading, or downgrading, your current copy of Tunnelblick will be put in the Trash before it is replaced.

After a few seconds, a new window will appear asking if you wish to launch Tunnelblick. Click the "Launch" button to launch Tunnelblick.

If your computer is already running Tunnelblick, you will be asked if you wish to close all connections and quit the current copy. Click the button to do so.

You will now see a window asking for an administrator username and password. Enter them and click "OK".

You may see a window asking if you wish to check for updates automatically. Click a button to indicate your selection.

When there are no configuration files in `~/Library/Application Support/Tunnelblick/Configurations` (which is usually the case the first time Tunnelblick is run by each user), the "Welcome to Tunnelblick" window will appear. You have three choices:
  * If you click "Install and edit sample configuration file”, Tunnelblick will create a sample OpenVPN configuration file at `~/Library/Application Support/Tunnelblick/Configurations/openvpn.conf`, then open it in `TextEdit` for you to modify. Tunnelblick will keep running, and, after you modify `openvpn.conf` to connect to your VPN, you can proceed to [Using Tunnelblick](QuickStartGuide#Using_Tunnelblick.md)

  * If you click "Quit”, Tunnelblick will quit without doing anything.

  * If you click "Open configuration folder", Tunnelblick will open a Finder window with `~/Library/Application Support/Tunnelblick/Configurations`, and then quit. Move or copy your OpenVPN configuration file(s) -- files with extensions of ".ovpn" or ".conf" -- to this window. If you have received key files or certificate files with your configuration file, move or copy them to this window also.

## Launching Tunnelblick ##
To launch Tunnelblick after setting up configuration and other files, double-click "Launch Tunnelblick" in the `Configurations` folder, or double-click Tunnelblick in the Applications folder.

## Using Tunnelblick ##
Once Tunnelblick has been launched, you control it from the Tunnelblick icon in the Status Bar at the top of your screen. The Tunnelblick icon is usually placed between the time and the Spotlight icon. When no VPN connection is active, the icon is dark, indicating a closed tunnel.

If you click on the icon, you'll see a drop down menu. The menu has
  * A "Connect” item for each .ovpn or .conf file
  * A "Details…" item which will open a window with details and an OpenVPN log for each connection
  * An "Options…" item which reveals several other choices:
    * Several preferences that control Tunnelblick's behavior
    * A "Check for Updates Now" item
    * An "About…" item
  * A "Quit" item

If you click on "Details…", a new window will appear with a tab for each configuration. Each tab includes preferences, the OpenVPN log, and several buttons.

You may use the standard keyboard shortcuts in the "Details…" window: Command-C, Command-X, and Command-V for copy, cut, and paste; and Command-A, Command-M, Command-W, and Command-Q to select all the text in the log that is currently being displayed, minimize the window to the dock, close the window, and quit the program.

## Connecting to a VPN ##
To connect to a VPN, either
  * Click on the "Connect" menu item for it's configuration, or
  * Click on the "Connect" button on the configuration's tab in the "Details…" window

To illustrate the connection being established, three dots will appear in the menu item, and the Tunnelblick icon will darken and lighten repeatedly. If the connection is successfully established, the Tunnelblick icon will change to show an open tunnel, and the "Connect..." menu item for the connection will change to "Disconnect...".

Depending on your setup, you may be asked for a passphrase or username/password combination. You can save your passphrase or password in Apple's Keychain by checking the appropriate checkbox.

The connection will be active as long as you do not end it or log out. Putting your computer to sleep will close the connection but upon waking up from sleep Tunnelblick will attempt to reestablish the connection.

## Disconnecting from a VPN ##
To disconnect from a VPN, either
  * Click on the "Disconnect" menu item for it's configuration, or
  * Click on the "Disconnect" button on the configuration's tab in the "Details…" window.

It usually takes a couple of seconds to disconnect from a VPN.

## Quitting Tunnelblick ##
You can quit Tunnelblick by:
  * Clicking on the Tunnelblick icon, then on "Quit"
  * Typing Command-Q (also known as Apple-Q) from the "Details…" (or "OpenVPN Log) window, or the "About…" window.

Tunnelblick will close all connections before it quits.

If you **don't** quit Tunnelblick before logging out, it will be started automatically upon login. Don't confuse this automatic launch of Tunnelblick upon login with the "automatically connect on launch” option, which causes a connection to be established when Tunnelblick is started.

## Preferences ##
The "Options…" submenu allows you to control several preferences. Click on one to change its status from checked to unchecked and vice-versa:
  * **Place Icon Near the Spotlight Icon**: If checked, the Tunnelblick icon will be positioned near the Spotlight icon at the extreme right of the screen. If unchecked, it will be placed to the left of the other icons at the time Tunnelblick is started.
  * **Monitor the Configuration Folder**: If checked, Tunnelblick will monitor the folder that contains configurations and react appropriately when configuration files are added or removed. If not checked, Tunnelblick not recognize added or removed configurations until it is restarted.
  * **Use Shadow Copies of Configuration Files**: If checked, Tunnelblick will create and use "shadow copies" of configuration files on the local hard drive. If not checked, the original of each configuration file will be used. Configuration files must have certain settings for security; if the configuration file is on a volume which does not allow these settings, shadow copies must be used so the copies can be secured. This happens automatically when the home folder is located on a network volume; it is not necessary to use this preference.

The "Details…" window allows you to control several preferences for each configuration separately:
  * **Automatically connect on launch**: If checked, Tunnelblick will connect using the configuration when Tunnelblick is launched. If not checked, the user must connect manually.
  * **Set nameserver**: If checked, Tunnelblick will use its standard scripts before and after a connection is made to save and restore the computer's DNS and WINS settings, and allow DNS and WINS settings to be "pushed" from the VPN server. If not checked, no save and restore will be done and the DNS and WINS settings will not be "pushed" from the VPN server.
  * **Monitor connection**: (Only available if "Set nameserver" is checked.) If checked, Tunnelblick will monitor the network and restart the connection if changes to the network DNS or WINS configurations are detected. If unchecked, or if "Set nameserver" is not checked, no monitoring will be done. Note: under certain circumstances, repeated and unnecessary restarts are peformed when "Monitor connection" is checked; unchecking it stops this from occurring.

For more details on "Set nameserver" see the following section.

There are many other preferences that control Tunnelblick's behavior. See [Preferences](Preferences.md).

## The Set Nameserver Check Box and DNS and WINS Settings ##
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

## What Tunnelblick Is ##
  * **Explanation 1**: Tunnelblick is a program that can be used to securely connect a Mac running OS X to a remote network or the Internet, bypassing untrusted networks, censorship, and eavesdropping. It does this by creating a "Virtual Private Network", or "[VPN](http://en.wiktionary.org/wiki/Virtual_Private_Network) `[`wiktionary.org`]`", to a VPN server using a program named "OpenVPN", which is included within the Tunnelblick application. When you connect through a VPN, your computer sends all network traffic through a "tunnel" to the VPN server, which then passes on your network traffic to a local network or the Internet. It is as if you were connecting to the network or Internet through the VPN server instead of your computer. Usually, all traffic between your computer and the VPN server is encrypted.

> VPNs are primarily used two ways, or sometimes both ways simultaneously:
    * To securely connect a computer to the Internet, even though it may be connecting through an untrusted network (a wireless network at a hotel or airport, for example); and
    * To securely connect a computer to a company's internal network or some part of it (a branch office, for example).

> In addition to Tunnelblick, you need access to a VPN server. Your company may provide one, or you can obtain VPN service from any of several VPN service providers, or you can use another one of your computers or a router to act as a VPN server.

  * **Explanation 2**: Tunnelblick is a ready-to-use Graphic User Interface (GUI) for OpenVPN on Mac OS X. It provides easy-to-use control of OpenVPN server and/or client connections.

> It runs on OS X Tiger (10.4), Leopard (10.5), and Snow Leopard (10.6). It comes as a ready-to-use Universal application with all necessary binaries and drivers (including OpenVPN and tun/tap) included. No additional installation is necessary -- just add your configuration and encryption information.

> Tunnelblick is free software licensed under the GNU General Public License (GPL) Version 2.

For more information, including wikis and a discussion group, see the [Tunnelblick home page](http://code.google.com/p/tunnelblick/).

## Document History ##
  * 2010-02-09 (Version 3.0b26)
    * Document created.
  * 2010-02-14
    * Minor edit
  * 2010-03-19
    * Minor edit

---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS