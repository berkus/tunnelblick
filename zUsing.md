This document describes how to use Tunnelblick version 3.2beta16 and later. For earlier versions, see [Using Tunnelblick 3.1](wUsing.md).



## Starting Tunnelblick ##
To launch Tunnelblick after setting up configuration and other files, double-click Tunnelblick in the Applications folder or double-click "Launch Tunnelblick" in the configurations folder.

If you do not quit Tunnelblick before logging out or shutting down your computer, it will automatically be launched the next time you log in.

## Quitting Tunnelblick ##
To quit Tunnelblick, click on the Tunnelblick icon in the menu bar at the top of your screen between the time and the Spotlight icon, then click on "Quit". Or type Command-Q when the Details or About window is at the front of the display.
  * When you quit Tunnelblick, all open connections will be closed except those for configurations which are set to automatically connect "when the computer starts".

  * If you quit Tunnelblick, it will not be launched automatically the next time you log in.

## Automatically Starting Tunnelblick Upon Login ##
Tunnelblick was designed as a persistent menu icon that survives reboots. To this end, it inserts itself into the login items when it is started and only removes itself from the login items when you choose Quit from the menu or Command-Q from the "Details” window or "About..." window. So if you just log out, shut down, or restart your computer, or it crashes, the next time you log in, Tunnelblick will automatically start. If you do not want Tunnelblick to start automatically, quit Tunnelblick before you log out, shut down, or restart.

## Normal Tunnelblick Operation ##
Once Tunnelblick has been launched, you control it from the Tunnelblick icon in the menu bar at the top of your screen. The Tunnelblick icon is usually placed between the time and the Spotlight icon. When no VPN connection is active, the icon is dark, indicating a closed tunnel:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-closed-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-closed-2010-02-04.png)

If you click on the icon, you'll see a drop down menu similar to the following:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-menu-2011-07-20.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-menu-2011-07-20.png)

There will be a "Connect” menu item for each available configuration (configurations in subfolders appear on submenus). Click on a "Connect" item to establish the corresponding VPN connection. To illustrate the connection being established, a dash will appear in the menu item and the Tunnelblick icon will darken and lighten repeatedly. If the connection is successfully opened, the icon will change to show an open tunnel:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png)

Depending on your setup, you may be asked for a passphrase or username/password combination. You can save your passphrase or username and password in Apple's Keychain by checking the appropriate checkbox.

The connection will be active as long as you do not end it or log out. (Tunnelblick will not close a connection for a configuration that is set up to automatically connect "when the computer starts" if you log out or quit Tunnelblick. The connection will remain open until your computer shuts down, sleeps, or you specifically disconnect it.)

Putting your computer to sleep will close the connection but upon waking up from sleep Tunnelblick will attempt to reestablish the connection.

If a connection error occurs, or in the unlikely event of an interface crash, Tunnelblick will terminate the VPN tunnel and record the error in the Console Log.

Use "Disconnect” from the drop-down menu to close the VPN connection. Use "Quit” to close all open connections<sup>*</sup> and quit the program and prevent Tunnelblick from starting itself at your next login at your computer.

<sup>*</sup> Tunnelblick will not close a connection for a configuration that is set up to automatically connect "when the computer starts" if you log out or quit Tunnelblick. The connection will remain open until your computer shuts down or you specifically disconnect it.

If Tunnelblick is running when you logout (or your computer crashes, or is shut down or restarted), then Tunnelblick will be started automatically upon login. To stop Tunnelblick from being started automatically upon login, be sure to quit Tunnelblick before logging out, either by using the "Quit” command, or by using Command-Q (Apple-Q) when the "Details” or "About…” window is active. (Don't confuse this automatic launch of Tunnelblick upon login with the "automatically connect on launch” option, which causes a connection to be established when Tunnelblick is launched.)

## The "VPN Details…" Window ##
When the Tunnelblick menu is displayed, if you click on "VPN Details…” a window similar to the following will appear:

<img width='420' height='274' src='http://tunnelblick.googlecode.com/files/using-tunnelblick-details-log-2011-07-20.png'>

This window has four sections: Configurations, Preferences, Appearance, and Info. Select the section by clicking on it in the top toolbar. The "Configurations" section is shown above.<br>
<br>
<h3>Configurations</h3>
The Configurations section has an entry for each Configurations on the left side. Tabs with the log and settings for the configuration selected on the left side are displayed on the right side. You may adjust the relative sizes of the left and right side by dragging the small dot between the two sides.<br>
<br>
The "Log" tab (shown above) displays the log for the configuration. A button allows you to copy the entire contents of the log to the Clipboard so you may paste it into an email or other document.<br>
<br>
<img width='420' height='274' src='http://tunnelblick.googlecode.com/files/using-tunnelblick-details-settings-2011-07-20.png'>

The "Settings" tab (shown above) allows you to see and modify several settings for the configuration:<br>
<br>
<ul><li>"Connect” specifies when the configuration should be connected:<br>
<ul><li>"Manually" specifies that you will connect the configuration manually;<br>
</li><li>"When Tunnelblick launches" specifies that the configuration to be connected when Tunnelblick is launched (started) ;<br>
</li><li>"When computer starts" specifies that the configuration to be connected when the computer starts. You can only choose "when the computer starts" for  automatic Tunnelblick VPN Configurations] or <a href='cCusDeployed.md'>"Deployed"</a> configurations</li></ul></li></ul>

<ul><li>"Set DNS/WINS: Set nameserver” causes scripts to be run before a connection is opened and after the connection is closed. The scripts save and restore DHCP DNS and WINS information. Other choices for "Set DNS/WINS" are:<br>
<ul><li>"Do not set nameserver", which does not change DNS settings;<br>
</li><li>"Set nameserver (3.1), which manipulates DNS settings the way that Tunnelblick 3.1 does;<br>
</li><li>"Set nameserver (3.0b10), which manipulates DNS settings the way that Tunnelblick 3.0b10 does; and<br>
</li><li>"Set nameserver (alternate 1)", which manipulates DNS settings in a different way that is more compatible with some configurations.</li></ul></li></ul>

<ul><li>"Monitor connection" causes the network connection to be monitored for changes. It is available only when "Set nameserver" or "Set nameserver 3.1" is selected. When a change is detected, the connection will be disconnected and reconnected.</li></ul>

<ul><li>"Show configuration on Tunnelblick menu" lets you show or not show the configuration in the menu that pops down when you click the Tunnelblick icon.</li></ul>

<ul><li>You may also select a sound to be played when a configuration connects or unexpectedly disconnects.</li></ul>

<blockquote>Additional settings may be examined and modified by clicking the "Advanced" button.)</blockquote>

"Connect" and "Disconnect" buttons will connect or disconnect the configuration selected on the left side of the window.<br>
<br>
A help button displays detailed help.<br>
<br>
At the bottom of the list of configurations on the left side of the window there are three small buttons:<br>
<br>
<ul><li>The "+" button guides you through the process of adding a new configuration.</li></ul>

<ul><li>The "-" button deletes the selected configuration. The username and password of a computer administrator is required to delete a configuration.</li></ul>

<ul><li>The "gear" button pops down a list of other actions to take using the selected configuration:</li></ul>

<img width='220' height='110' src='http://tunnelblick.googlecode.com/files/using-tunnelblick-showing-gear-2011-07-20.png'>

<h3>Preferences</h3>
The "Preferences" section of the "VPN Details..." window allows you to modify Tunnelblick's behavior, check for updates, and reset disabled warnings:<br>
<br>
<img width='420' height='274' src='http://tunnelblick.googlecode.com/files/using-tunnelblick-preferences-section-2011-06-24.png'>

<h3>Appearance</h3>
The "Appearance" section of the "VPN Details..." window allows you to modify Tunnelblick's appearance:<br>
<br>
<img width='420' height='274' src='http://tunnelblick.googlecode.com/files/using-tunnelblick-appearance-section-2011-06-27.png'>

<h3>Info</h3>
The "Info" section of the "VPN Details..." window displays information about the Tunnelblick program and the people who have contributed to it:<br>
<br>
<img width='420' height='274' src='http://tunnelblick.googlecode.com/files/using-tunnelblick-info-section-2011-06-24.png'>

(Note: the credits scroll to reveal additional contributors, so not all contributors are displayed in the above screenshot.)<br>
<br>
<h2>Keyboard Shortcuts</h2>
You may use the standard keyboard shortcuts in the "VPN Details..." window:<br>
<table><thead><th>Command-C</th><th>Copy</th></thead><tbody>
<tr><td>Command-X</td><td>Cut</td></tr>
<tr><td>Command-V</td><td>Paste</td></tr>
<tr><td>Command-A</td><td>Select all the text in the log</td></tr>
<tr><td>Command-M</td><td>Minimize the window to the dock</td></tr>
<tr><td>Command-W</td><td>Close the window</td></tr>
<tr><td>Command-Q</td><td>Quit Tunnelblick</td></tr></tbody></table>

<h2>Using More than One VPN Configuration</h2>
You can have any number of configurations installed; each of the configurations will be available in the drop down menu and shown as a separate entry in the "Details” window.<br>
<br>
<h2>Connecting to More than One VPN Simultaneously</h2>
Tunnelblick can maintain multiple simultaneous open connections to different VPNs.<br>
<br>
However, this is for experts only:<br>
<br>
<ul><li>If you use "Set nameserver” (which uses standard scripts to save/change/restore DNS resolution data), on one or more connections your DNS settings may not be saved and restored properly and DNS might or might not work. It depends on the order in what DNS settings you want to use and which connections are opened and closed. Connections may close and be reopened because of communications errors over which you have no control, which can cause unpredictable results. Not recommended.<br>
</li><li>If you don't use "Set nameserver”, and your customized configuration files are suitably written to work together with custom scripts, things can work. But if you don't handle the DNS and routing settings properly, lots of things could go wrong. So this isn't recommended either unless you really know what you're doing and have a NEED to connect to multiple VPNs simultaneously.<br>
</li><li>VPN administrators might not be happy that you are connecting their networks together. Most VPN client software limits you to a single connection, probably for that reason.</li></ul>

<h2>Command-Line Interface</h2>
Tunnelblick also contains openvpnstart, an OS X command line interface to OpenVPN which provides a scriptable way to create and destroy OpenVPN tunnels. (But Tunnelblick also has support for <a href='cAppleScriptSupport.md'>!AppleScript</a>.) openvpnstart is located in Tunnelblick.app/Contents/Resources. For details on using openvpnstart, run it from a Terminal window with no arguments. When a connection attempt is made, Tunnelblick inserts the openvpnstart command line into the log; it can be copied from there for use in your own shell scripts.<br>
<br>
<hr />

<h3>PLEASE USE THE <a href='https://groups.google.com/forum/#!forum/tunnelblick-discuss'>TUNNELBLICK DISCUSSION GROUP</a> FOR COMMENTS OR QUESTIONS</h3>