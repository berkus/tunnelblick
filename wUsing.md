This document describes how to use Tunnelblick version 3.1.



## Starting Tunnelblick ##
To launch Tunnelblick after setting up configuration and other files, double-click Tunnelblick in the Applications folder or double-click "Launch Tunnelblick" in the configurations folder.

If you do not quit Tunnelblick before logging out or shutting down your computer, it will automatically be launched the next time you log in.

## Quitting Tunnelblick ##
To quit Tunnelblick, click on the Tunnelblick icon in the menu bar at the top of your screen between the time and the Spotlight icon, then click on "Quit". Or type Command-Q when the Details or About window is at the front of the display.
  * When you quit Tunnelblick, all open connections will be closed except those for configurations which are set to automatically connect "when the computer starts".

  * If you quit Tunnelblick, it will not be launched automatically the next time you log in.

## Normal Tunnelblick Operation ##
Once Tunnelblick has been launched, you control it from the Tunnelblick icon in the menu bar at the top of your screen. The Tunnelblick icon is usually placed between the time and the Spotlight icon. When no VPN connection is active, the icon is dark, indicating a closed tunnel:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-closed-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-closed-2010-02-04.png)

If you click on the icon, you'll see a drop down menu similar to the following:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-menu-2010-07-29.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-menu-2010-07-29.png)

There will be a "Connect” menu item for each available configuration (configurations in subfolders appear on submenus). Click on a "Connect" item to establish the corresponding VPN connection. To illustrate the connection being established, a dash will appear in the menu item and the Tunnelblick icon will darken and lighten repeatedly. If the connection is successfully opened, the icon will change to show an open tunnel:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png)

Depending on your setup, you may be asked for a passphrase or username/password combination. You can save your passphrase or username and password in Apple's Keychain by checking the appropriate checkbox.

The connection will be active as long as you do not end it or log out. (Tunnelblick will not close a connection for a configuration that is set up to automatically connect "when the computer starts" if you log out or quit Tunnelblick. The connection will remain open until your computer shuts down, sleeps, or you specifically disconnect it.)

Putting your computer to sleep will close the connection but upon waking up from sleep Tunnelblick will attempt to reestablish the connection.

If a connection error occurs, or in the unlikely event of an interface crash, Tunnelblick will terminate the VPN tunnel and record the error in the Console Log.

Use "Disconnect” from the drop-down menu to close the VPN connection. Use "Quit” to close all open connections<sup>*</sup> and quit the program and prevent Tunnelblick from starting itself at your next login at your computer.

<sup>*</sup> Tunnelblick will not close a connection for a configuration that is set up to automatically connect "when the computer starts" if you log out or quit Tunnelblick. The connection will remain open until your computer shuts down or you specifically disconnect it.

If Tunnelblick is running when you logout (or your computer crashes, or is shut down or restarted), then Tunnelblick will be started automatically upon login. To stop Tunnelblick from being started automatically upon login, be sure to quit Tunnelblick before logging out, either by using the "Quit” command, or by using Command-Q (Apple-Q) when the "Details” or "About…” window is active. (Don't confuse this automatic launch of Tunnelblick upon login with the "automatically connect on launch” option, which causes a connection to be established when Tunnelblick is launched.)

## The "Options…" Submenu ##
When the Tunnelblick menu is displayed, if you hover over "Options", the Options Submenu appears:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-options-menu-2010-07-29.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-options-menu-2010-07-29.png)

Click on an item in the Options Submenu to change a [preference](wPrefs.md), add a configuration, check for updates, or display the "About" window.

Some deployed versions of Tunnelblick do not display the Options Submenu, in which case the "Options" menu item is replaced by "About Tunnelblick..."

## The "Details" Window ##
When the Tunnelblick menu is displayed, if you click on "Details…” a window similar to the following will appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-details-2010-10-16.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-details-2010-10-16.png)

The window will contain a tab for each configuration and the title of the window will show the name of the currently selected configuration and its availability (Private, Shared, or Deployed).

Each tab in the window contains a pane with the OpenVPN log for the connection and controls that provide options for that connection. The title of the tab shows the current status of the configuration and, if connected, the time since it was connected.

When there are many connections, a tab for each connection will not fit on the screen. In this case, the "Details…" window will look similar to the following:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-details-left-nav-2010-10-16.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-details-left-nav-2010-10-16.png)

In this version of the "Details…" window, there is an entry for each connection on the left side. The tab with the OpenVPN log and controls for the connection selected on the left side will be displayed on the right side. You may adjust the relative sizes of the left and right side by dragging the small dot between the two sides.

The controls for each configuration (regardless of which window is displayed) are:

  * "Automatically connect” causes the configuration to be connected when Tunnelblick is launched (started) or when the computer starts, as indicated. You can only choose "when the computer starts" for [Tunnelblick VPN Configurations](cConfigT.md) or ["Deployed"](cCusDeployed.md) configurations; that choice will be dimmed for configurations based on .ovpn or .conf files that are not "Deployed".

  * "Set nameserver” causes scripts to be run before a connection is opened and after the connection is closed. The scripts save and restore DHCP DNS and WINS information. This is involved in Tunnelblick's setup for the configuration. See [Configuring Tunnelblick](cConfigT.md). Other choices in the drop-down list are:
    * "Do not set nameserver", which does not change DNS settings;
    * "Set nameserver (3.0b10), which manipulates DNS settings the way that Tunnelblick 3.0b10 does; and
    * "Set nameserver (alternate 1)", which manipulates DNS settings in a different way that is more compatible with some configurations.

  * "Monitor connection" causes the network connection to be monitored for changes. It is available only when "Set nameserver" is selected. When a change is detected, the connection will be disconnected and reconnected.  This checkbox is involved in Tunnelblick's setup for the configuration. See [Configuring Tunnelblick](cConfigT.md).

The "Details” window also contains five buttons:

  * "Clear log” clears the OpenVPN log for the connection being displayed.

  * An "Edit configuration” or "Examine configuration" button will start TextEdit with the OpenVPN configuration file for the connection being displayed so it can be examined or edited. If you modify a configuration file, you will need the username and password of a computer administrator to connect using the modified configuration file. Shared and Deployed configurations may only be examined, not edited. (To modify a shared configuration, make it private, modify it, then make it shared again.)

  * A "Share configuration" or "Make configuration private" button will be available if the configuration is a [Tunnelblick VPN Configuration](cConfigT.md). Sharing a configuration makes it available to all users of a computer; making a configuration private makes it available only to the currently logged-in user. The button will be dimmed if the configuration is a .conf or .ovpn file, or is a "Deployed" configuration. Changing the availability of a configuration requires a computer administrator username and password.

  * "Connect” opens the connection.

  * "Disconnect” closes the connection.

## Keyboard Shortcuts ##
You may use the standard keyboard shortcuts in the "Details" window:
|Command-C|Copy|
|:--------|:---|
|Command-X|Cut|
|Command-V|Paste|
|Command-A|Select all the text in the log|
|Command-M|Minimize the window to the dock|
|Command-W|Close the window|
|Command-Q|Quit Tunnelblick|

## The "About…" Window ##
Click on the Tunnelblick icon in the menu bar at the top of your screen between the time and the Spotlight icon, then (if it is visible) click on "Options", then on "About…” to open a window with information about the versions of Tunnelblick and OpenVPN that are running and a link to the Tunnelblick website.

## Using More than One VPN Configuration ##
You can have any number of configurations installed; each of the configurations will be available in the drop down menu and shown as a separate tab (or left-side entry) in the "Details” window.

## Connecting to More than One VPN Simultaneously ##
Tunnelblick can maintain multiple simultaneous open connections to different VPNs.

However, this is for experts only:

  * If you use "Set nameserver” (which uses standard scripts to save/change/restore DNS resolution data), on one or more connections your DNS settings may not be saved and restored properly and DNS might or might not work. It depends on the order in what DNS settings you want to use and which connections are opened and closed. Connections may close and be reopened because of communications errors over which you have no control, which can cause unpredictable results. Not recommended.
  * If you don't use "Set nameserver”, and your customized configuration files are suitably written to work together with custom scripts, things can work. But if you don't handle the DNS and routing settings properly, lots of things could go wrong. So this isn't recommended either unless you really know what you're doing and have a NEED to connect to multiple VPNs simultaneously.
  * VPN administrators might not be happy that you are connecting their networks together. Most VPN client software limits you to a single connection, probably for that reason.

## Automatically Starting Tunnelblick Upon Login ##
Tunnelblick was designed as a persistent menu icon that survives reboots. To this end, it inserts itself into the login items when it is started and only removes itself from the login items when you choose Quit from the menu or Command-Q from the "Details” window or "About..." window. So if you just log out, shut down, or restart your computer, or it crashes, the next time you log in, Tunnelblick will automatically start. If you do not want Tunnelblick to start automatically, quit Tunnelblick before you log out, shut down, or restart.

## Command-Line Interface ##
Tunnelblick also contains openvpnstart, an OS X command line interface to OpenVPN which provides a scriptable way to create and destroy OpenVPN tunnels. openvpnstart is located in Tunnelblick.app/Contents/Resources. For details on using openvpnstart, run it from a Terminal window with no arguments. When a connection attempt is made, Tunnelblick inserts the openvpnstart command line into the log; it can be copied from there for use in your own shell scripts.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###