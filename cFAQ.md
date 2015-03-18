

## What is Tunnelblick? ##
  * **Explanation 1**: Tunnelblick is a program that can be used to securely connect a Mac running OS X to a remote network or the Internet, bypassing untrusted networks, censorship, and eavesdropping. It does this by creating a "Virtual Private Network", or "[VPN](http://en.wiktionary.org/wiki/Virtual_Private_Network) `[`wiktionary.org`]`", to a VPN server using a program named "OpenVPN", which is included within the Tunnelblick application. When you connect through a VPN, your computer sends all network traffic through a "tunnel" to the VPN server, which then passes on your network traffic to a local network or the Internet. It is as if you were connecting to the network or Internet through the VPN server instead of your computer. All traffic between your computer and the VPN server is encrypted.

> VPNs are primarily used two ways, or sometimes both ways simultaneously:
    * To securely connect a computer to the Internet, even though it may be connecting through an untrusted network (a wireless network at a hotel or airport, for example); and
    * To securely connect a computer to a company's internal network or some part of it (a branch office, for example).

> In addition to Tunnelblick, you need access to a VPN server. Your company may provide one, or you can obtain VPN service from any of several VPN service providers, or you can use another one of your computers or a router to act as a VPN server. See [Getting VPN Service](cGettingVPNService.md) for details.

  * **Explanation 2**: Tunnelblick is a ready-to-use Graphic User Interface (GUI) for OpenVPN on Mac OS X. It provides easy-to-use control of OpenVPN server and/or client connections.

> It runs on OS X Tiger (10.4), Leopard (10.5), and Snow Leopard (10.6). It comes as a ready-to-use Universal application with all necessary binaries and drivers (including OpenVPN and tun/tap) included. No additional installation is necessary -- just add your configuration and encryption information.

> Tunnelblick is free software licensed under the GNU General Public License (GPL) Version 2.

## Where is the documentation? ##
The Tunnelblick disk image includes a link to the [Tunnelblick Documentation](Documentation.md). There is also help available in Tunnelblick's main window, the VPN Details… window.

## Does Tunnelblick work on Snow Leopard? Leopard? Tiger? Lion? Mountain Lion? Panther? Intel? PowerPC? ##
Yes. Tunnelblick is a Universal 32-bit application, so it runs as an application in 32-bit mode on both Intel and PowerPC Macs under Tiger, Leopard, Snow Leopard, Lion, and Mountain Lion, under 32-bit and 64-bit kernels. It includes 32/64-bit versions of tun.kext and tap.kext. Tiger, Leopard, and Snow Leopard's 32-bit kernel use the 32-bit tun/tap, and Snow Leopard's 64-bit kernel, Lion, and Mountain Lion use the 64-bit tun/tap.

Mountain Lion works best with Tunnelblick 3.3beta36 and up, but can be run on 3.3beta21 and with some setups, on 3.2.8.

Panther requires a very old version, [Tunnelblick 2.0.1](http://tunnelblick.googlecode.com/files/Tunnelblick-Panther-2.0.1.dmg).

## What else do I need? ##
You need a VPN server to connect to. It could be a server at your company or at a VPN service provider, or it could be a VPN that you have set up yourself at home. See [Getting VPN Service](cGettingVPNService.md) for details.

What else you need depends on your situation:
  * If you have a "deployed" version of Tunnelblick (usually from a company or VPN service provider), you may not need anything else -- everything is usually included in the customized version of the Tunnelblick application that is distributed.
  * Otherwise, you need either a "configuration file" or enough information about the VPN to edit the sample configuration file that Tunnelblick will offer to install. You will probably also need certificate and key files for encryption. Your company or VPN service provider should provide them.

## How do I know the VPN is working? ##
Tunnelblick indicates that the VPN is connected by showing the "open" tunnel in your menu bar (usually near the Spotlight icon).

![http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png)

But whether all traffic will be directed through the VPN depends on the settings in the OpenVPN configuration file. If the "redirect-gateway def1" option appears, then all traffic should go through the VPN.

An easy way to check if web traffic is going through the VPN is to go to http://whatismyipaddress.com -- it should give the IP address of the OpenVPN server, not the address of your (OpenVPN client) computer. If it doesn't, then add the "redirect-gateway def1" option to your OpenVPN configuration file.

## What if the Internet doesn't work after I make a connection? ##
See [Connects to the VPN, but doesn't work](cConnectedBut.md).

## How do I verify a download's SHA-1 checksum? ##
To get the "SHA-1" checksum of a file, use the following command in Terminal:

```
/usr/bin/openssl  sha1  path-to-the-file
```
For example:

```
/usr/bin/openssl  sha1  /Users/johnsmith/Downloads/Tunnelblick_3.0.dmg
```

## Where can I get old versions of Tunnelblick? ##
All available versions of Tunnelblick are available on the [Downloads](DownloadsEntry.md) page.

## What is a "deployed" version of Tunnelblick? ##
A "deployed" version of Tunnelblick is a customized version of the program, which includes everything you need to connect to a VPN: the program itself, configuration file(s), and key and certificate files for encryption.

If you download Tunnelblick from [this website](http://code.google.com/p/tunnelblick/), it is _not_ a deployed version. You must also have configuration, key, and certificate files, which should be provided to you by your company or your VPN service provider.

See [Deploying Tunnelblick](cDeployingTunnelblick.md) for detailed information about deployed versions of Tunnelblick.

## How do I install Tunnelblick? ##
Download the latest disk image. Double-click it and a window will open with the Tunnelblick icon and the words "Double-click to begin". Double-click the Tunnelblick icon and you will be guided through the process of copying Tunnelblick to your Applications folder.  Reinstalls, upgrades, and downgrades will be recognized and the old version of the program is moved to the Trash before installing the new version.

## I've installed Tunnelblick. Now what? ##
Start Tunnelblick by double-clicking it in Applications. It will step you through the process of setting up configuration files. When Tunnelblick is running, it will display the Tunnelblick icon in the status bar at the top of the screen on the right. Usually, the icon is located immediately between the time display and the Spotlight icon.
Click on the Tunnelblick icon to reveal the Tunnelblick menu, then click on a configuration to connect using it, or click on "VPN Details…" for a window with details for each configuration.

## How do I uninstall Tunnelblick? ##
See [Uninstalling Tunnelblick](cInstall#Uninstalling_Tunnelblick.md).

## How do I revert to an earlier version of  Tunnelblick? ##
For Tunnelblick 3.1beta18 (2010-010-16) and later, download the disk image with the version you wish to install (all available versions are on the [Downloads Page](DownloadsEntry.md). Double-click it and a window will open with the Tunnelblick icon and the words "Double-click to begin". Double-click the Tunnelblick icon and you will be guided through the process.  Reinstalls, upgrades, and downgrades will be recognized and the old version of the program is moved to the Trash before installing the new version.

For earlier versions of Tunnelblick, you'll have to drag your existing version (usually found in /Applications) to the Trash and then drag and drop the version on the disk image to /Applications.

## How do I update Tunnelblick? ##
Each time Tunnelblick is launched, it checks for updates automatically (if that was specified when Tunnelblick was installed) and displays a notice that an update is available. (It also checks every week if it is running for more than a week.)

(Note: Due to a bug in older versions of Tunnelblick, update notices are sometimes not visible. For versions of Tunnelblick earlier than 3.0b16, the user must display the "VPN Details…" window and click in that window for the popup window to appear. For versions of Tunnelblick earlier than 3.0b24, the user must display the "VPN Details…" window for the popup window to appear. For version 3.0b24 and later, update notices will be visible without any user action.)

If automatic checking for updates is not enabled, there are three ways to update Tunnelblick manually:

_Whichever method you chose, you will need an administrator username/password the first time a new copy of Tunnelblick is run._ All configurations and preferences will be used by the new version (even if it is a "deployed" version).

  * You can update to the latest _stable_ version of Tunnelblick by starting Tunnelblick, selecting "Options…" from the Tunnelbilck menu, then selecting "Check for Updates Now". If an update is available, you will be guided through the update process. If you install an update, your old version will be moved to the Trash.

  * If you don't see an "Options…" menu selection, you are using a very old version of Tunnelblick. You'll need to download the version you wish to use (stable or beta) and follow the "[How do I install Tunnelblick?](#How_do_I_install_Tunnelblick?.md)" instructions above.

  * If you are feeling a bit more adventurous, go to the [Downloads page](DownloadsEntry.md) and download the latest beta (experimental) version. Then follow the "[How do I install Tunnelblick?](#How_do_I_install_Tunnelblick?.md)" instructions above.

## Why does Tunnelblick need root privileges? ##
Tunnelblick needs root privileges the first time it is run for two reasons:
  1. It modifies ownership and privileges on parts of the Tunnelblick application itself to make it secure; and
  1. It modifies its "openvpnstart" binary to run as root so it can start OpenVPN as root.

OpenVPN needs root privileges because it needs to modify network settings when configuring network devices, changing routes, and adding and removing nameservers. Because we don't want you to enter your computer administrator password every time you start a VPN connection, Tunnelblick comes with the "openvpnstart" setuid root binary that allows you to do exactly one thing: start a VPN connection with super user rights.

Tunnelblick also needs root privileges to secure configuration files. If a configuration file is not owned by root, Tunnelblick asks for an administrator username/password so it can change the file's ownership to root before making a connection using that configuration file.

## Why does Tunnelblick change the ownership of the configuration files to root? ##
This is a security issue. OpenVPN configuration files allow you to specify up/down scripts which will be executed with root privileges every time a VPN connection is started or stopped. If the configuration files were owned by the local user, anyone could execute arbitrary code as root by inserting an 'up' directive to the configuration file and pointing it to a (malicious) shell script. Therefore, when a configuration file is first used, Tunnelblick asks for a computer administrator's username and password and uses them to change the ownership of the configuration file to root, so it is protected against unnoticed and possibly malicious changes. If new configuration files are added, Tunnelblick will ask for a computer administrator's username and password to change the ownership of the new file to root before the first use of each new configuration file.

## Why are routes not restored when closing my VPN connection? ##
You are probably using the 'user' or 'group' directive in your OpenVPN client configuration file. If you use it, the OpenVPN process will drop privileges after startup which is additional security measure. However, OpenVPN needs root privileges for restoring the route back to their original state. In short: don't use it.

As of version 3.0b22, Tunnelblick contains the "openvpn-down-root.so" plugin for OpenVPN. Together with a per-configuration preference, this allows the use of 'user' and 'group'. See [Using Tunnelblick](UsingTunnelblick.md) for details on how to do this.

## Why are some checkboxes or buttons dimmed and disabled? ##
Under certain circumstances,  checkboxes or buttons may be disabled and will appear dimmed -- nothing happens when you click on them. Buttons and checkboxes are disabled when they cannot be used. Examples (from the VPN Details… window):
  * "Monitor connection" is disabled unless "Set nameserver" is selected, because "Set nameserver" is required in order to monitor the connection.
  * "Share configuration" is disabled when the configuration is not a Tunnelblick VPN Configuration because only Tunnelblick VPN Configurations may be shared.
  * "Disconnect" is disabled when a configuration is not connected, and "Connect" is disabled when it is already connected.
  * "when computer starts" is disabled unless a configuration is shared or Deployed, because only shared or Deployed configurations may be automatically connected when the computer starts.
  * "when Tunnelblick launches" and "when computer starts" are disabled unless "automatically connect" is checked, because they areonly have meaning when it is checked.
  * "automatically connect", "Set nameserver", "Monitor connection", "Share configuration", and "Make configuration private" are disabled when "when computer starts" is selected. This is because you cannot directly modify them without administrator approval. To modify them, select "when Tunnelblick launches" (which will require an administrator username and password), change the settings to be the way you want, then select "when computer starts" (which will again require administrator approval).

## Why are some checkboxes or buttons missing? ##
  * You are using an older version of Tunnelblick which doesn't implement that checkbox or button; or
  * You are using a "deployed" version of Tunnelblick, and the deployer has specified that that checkbox or button should not be available; or
  * The button has a different label because it is being used for different purpose. Examples:
    * There is one button which displays "Edit configuration" or "Examine configuration" depending on whether you can edit (modify) the configuration, or only examine it. To edit a configuration, you must have write permissions on the folder which contains the configuration, and must be able to write to the configuration file. Non-administrator users of "Deployed" versions of Tunnelblick may be prevented from editing configurations by the deployer. Shared configurations may not be edited directly -- make the configuration private, edit it, and then share it to have this effect.
    * There is one button which displays either "Make configuration private" or "Share configuration". If the configuration is already being shared, it shows "Make configuration private". Otherwise, the button shows "Share configuration". Note that if the configuration is part of a "Deployed" version of Tunnelblick, or is not a Tunnelblick VPN Configuration, the button will be disabled (dimmed) because it cannot be shared.

## What version of OpenVPN does Tunnelblick include? ##
You can check the version of OpenVPN included in your copy of Tunnelblick by starting Tunnelblick, then selecting "Options…" from the Tunnelblick menu, then selecting "About…".

## Where can I go if my question is not answered here? ##
Take a look at the documents available in [Tunnelblick](Documentation.md) and at the [OpenVPN FAQ](http://openvpn.net/index.php/open-source/faq.html). If you don't find an answer, try the [Tunnelblick Discussion Group](https://groups.google.com/forum/#!forum/tunnelblick-discuss).


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS