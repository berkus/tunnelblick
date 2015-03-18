

**Special note for those who may have installed RaptorVPN or Urban Shield VPN or other VPN software**: These installations have backups that must be removed before installing Tunnelblick. See [this Discussion Group thread](https://groups.google.com/d/topic/tunnelblick-discuss/s368xGP5Qpk/discussion).


## Installing Tunnelblick and Getting it Set Up ##
Here is what you need to get started using Tunnelblick:
  * Access to a VPN server -- your computer is one end of the tunnel and the VPN server is the other end. For more information, see [Getting VPN Service](cGettingVPNService.md).
  * A copy of the Tunnelblick installation disk image. You can get one from the [Downloads page](DownloadsEntry.md).
  * A [Tunnelblick VPN Configuration](cConfigT.md) or an OpenVPN configuration file together with key and certificate files for encryption. You get these from whoever set up your VPN -- usually your company or a VPN service provider (see [Getting VPN Service](cGettingVPNService.md)).
  * The username and password of an administrator for your computer.

To get started, double-click the disk image.

You may see a message saying that "'Tunnelblick.app' is an application downloaded from the Internet. Are you sure you want to open it?". Click "Open".

A window will open. Double-click the Tunnelblick icon in the window to start the installation process.

You will be asked if you want to install/reinstall/upgrade/downgrade Tunnelblick. Enter an administrator username and password and click "Install" to install Tunnelblick to your Applications folder. If you are reinstalling, upgrading, or downgrading, your current copy of Tunnelblick will be put in the Trash before it is replaced.

After a few seconds, a new window will appear asking if you wish to launch Tunnelblick. Click the "Launch" button to launch Tunnelblick.

If your computer is already running Tunnelblick, you will be asked if you wish to close all connections and quit the current copy. Click the button to do so.

You may see a window asking if you wish to check for updates automatically. Click a button to indicate your selection.

When there are no configurations (which is usually the case the first time Tunnelblick is run), the "Welcome to Tunnelblick" window will appear. Follow the instructions to add configurations.

## Launching Tunnelblick ##
To launch Tunnelblick:
  * Double-click Tunnelblick in the Applications folder or
  * Double-click "Launch Tunnelblick" in the `Configurations` folder
If Tunnelblick is running when you log out, shut down, or restart your computer, it will automatically be launched when you log in.

## Using Tunnelblick ##
Once Tunnelblick has been launched, you control it from the Tunnelblick icon in the Status Bar at the top of your screen. The Tunnelblick icon is usually placed between the time and the Spotlight icon. When no VPN connection is active, the icon is dark, indicating a closed tunnel.

If you click on the icon, you'll see a drop down menu. The menu has
  * A status line showing how many configurations are connected. If there are any configurations that are connected, this line changes to allow you to disconnect all active configurations.
  * A "Connect” item for each configuration that has been set up. If there are no configurations, an "Add a configuration…" item will appear
  * An "Add a Configuration…" item which guides you through the process of adding a new configuration
  * A "VPN Details…" item which will open a window in which you can
    * Manage your configurations (add, delete, rename, duplicate, etc.)
    * See and modify settings for each configuration
    * See the log for each configuration
    * See and modify Tunnelblick preferences
    * See information about Tunnelblick
  * A "Quit" item

You may use the standard keyboard shortcuts in the "VPN Details…" window: Command-C, Command-X, and Command-V for copy, cut, and paste; and Command-A, Command-M, Command-W, and Command-Q to select all the text in the log that is currently being displayed, minimize the window to the dock, close the window, and quit the program.

## Connecting to a VPN ##
To connect to a VPN, either
  * Click on the "Connect" menu item for it's configuration, or
  * Click on the "Connect" button with the configuration selected on the left in the "VPN Details…" window.

To illustrate the connection being established, three dots will appear in the menu item, and the Tunnelblick icon will darken and lighten repeatedly. If the connection is successfully established, the Tunnelblick icon will change to show an open tunnel, and the "Connect..." menu item for the connection will change to "Disconnect...".

Depending on your setup, you may be asked for a passphrase or username/password combination. You can save your passphrase or password in Apple's Keychain by checking the appropriate checkbox.

The connection will be active as long as you do not end it or log out. Putting your computer to sleep will close the connection but upon waking up from sleep Tunnelblick will attempt to reestablish the connection.

## Disconnecting from a VPN ##
To disconnect from a VPN, either
  * Click on the "Disconnect" menu item for it's configuration, or
  * Click on the "Disconnect" button with the configuration selected on the left in the "VPN Details…" window.
  * Quit Tunnelblick. All connections that are not marked "automatically connect when the computer starts" will be disconnected before Tunnelblick quits.

It usually takes a couple of seconds to close Tunnelblick.

## Quitting Tunnelblick ##
You can quit Tunnelblick by:
  * Clicking on the Tunnelblick icon, then on "Quit"
  * Typing Command-Q (also known as Apple-Q) from the "VPN Details…" window.

Tunnelblick will close all connections that are not set to "automatically connect when the computer starts" before it quits.

## Starting Tunnelblick Automatically ##
If you **don't** quit Tunnelblick before logging out, it will be started automatically upon login. Don't confuse this automatic launch of Tunnelblick upon login with the "automatically connect” options, which cause a connection to be established when Tunnelblick is launched or when the computer is started or restarted.

If you have configurations that are marked "automatically connect when the computer starts", they will be connected whenever your computer starts or restarts. This is done without launching Tunnelblick, however, and if/when you login, there will be no indication that the connection is active unless you launch Tunnelblick (or it is launched automatically when you log in). When Tunnelblick is running, it will show the status of, and you will be able to control, any connections that were established when the computer started.

## Preferences and Settings ##
The "VPN Details…" window allows you to control Tunnelblick preferences as well as settings for each configuration. Default preferences and settings may be used except in unusual circumstances. VPN settings that are often modified include:
  * **Set nameserver**: If selected, Tunnelblick will use its standard scripts before and after a connection is made to save and restore the computer's DNS and WINS settings, and allow DNS and WINS settings to be "pushed" from the VPN server or retreived from a DHCP server at the other end of the tunnel. If not checked, no save and restore will be done and the DNS and WINS settings will not be modified by Tunnelblick. (They may, however, be modified by customized up/down scripts.)
  * **Monitor connection**: If checked, Tunnelblick will monitor the network and restart the connection if certain changes to the network DNS or WINS configurations are detected. If unchecked no monitoring will be done. Note: under certain circumstances, repeated and unnecessary restarts are peformed when "Monitor connection" is checked; unchecking it stops this from occurring.

For more details on "Set nameserver" see the following section.

There are other preferences that control Tunnelblick's behavior. See [Preferences](zPrefs.md).

## The "Set Nameserver" Check Box and DNS & WINS Settings ##
If you are using DHCP, wish to use DNS and WINS servers at the far end of the tunnel when connected, and the VPN server you are connecting to "pushes" DNS and WINS settings to your client or your client obtains DNS and WINS settings from a DHCP server at the far end of the tunnel, select "Set nameserver". (This is the situation for most users.)

If you are using DHCP, wish to use your original DNS and WINS servers when connected, and the VPN server you are connecting to does not "push" DNS or WINS settings to your client, select "Do not set nameserver".

If you are using manual settings, different versions of OS X behave differently. This is due to a change in network behavior in Snow Leopard and is beyond the scope of this project to fix.

  * If you're using Leopard (10.5) or Tiger (10.4), then it is possible to use the VPN-server-supplied DNS and WINS settings **in addition to** your manual settings by selecting "Set nameserver" box. However, your manual settings will always take precedence over any VPN server-supplied settings.  If "Do not set nameserver" is selected, you will continue to use only your manually-configured settings and any VPN server-supplied settings will be ignored. "Take precedence" means that the manual DNS server will be used for all DNS queries unless it fails to answer, in which case the VPN server-supplied DNS server will be used.

  * If you are using Snow Leopard (10.6), then your manual DNS and WINS settings will **always** be used, and no aggregation of configurations will be performed.

  * If you set your DNS servers manually, then regardless of the state of "Set nameserver", your manual DNS servers will always be the only ones used.

  * If you set your Search Domain(s) manually, then regardless of the state of "Set nameserver", your manual Search Domains will always be the only ones used.

  * If you set your WINS servers manually, then regardless of the state of "Set nameserver", your manual WINS servers will always be the only ones used.

  * Each of these settings is independent of the others: if "Set nameserver" is selected, those settings not configured manually will be replaced by the settings obtained from the VPN server.  If "Do not set nameserver" is selected, then as with Leopard/Tiger, no DNS/WINS settings will be applied.

**If your situation is not described above** (e.g., if you use manual DNS settings and wish to use DNS servers at the far end of a tunnel when connected, or you wish to use the OS X ability to use different nameservers for different domains), you must create your own up/down scripts and select "Do not set nameserver".


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS