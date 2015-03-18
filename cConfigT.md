

<font color='red'>Stop</font> if you have a ["Deployed" version](cCusDeployed.md) of Tunnelblick. It comes already set up -- you do no need to do anything more. Just [start using it](zUsing.md) and enjoy!

<font color='red'>Stop</font> if you have purchased VPN service from a VPN service provider. They should provide you with configuration files and instructions on how to use them with Tunnelblick.

<font color='red'>Stop</font> if you have VPN service from a corporate or other network provided by your employer. Your network manager or IT department should provide you with configuration files and instructions on how to use them with Tunnelblick.

<font color='red'>Stop</font> if want details about the structure of a Tunnelblick VPN Configuration, see [".tblk" Details](cPkgs.md).

The rest of this document is for everyone else.

## Setting Up Configurations ##
It is not enough to install Tunnelblick:  you also need to tell Tunnelblick **_how to connect_** to a VPN.

You tell Tunnelblick how to connect to a VPN with a configuration file. Tunnelblick can use two types of configuration files:
  * **Tunnelblick VPN Configurations.** A Tunnelblick VPN Configuration contains all of the information Tunnelblick needs to connect to one or more VPNs. A Tunnelblick VPN Configuration contains one or more OpenVPN configuration files, and may contain key, certificate, and script files. Everything needed is contained within the Tunnelblick VPN Configuration. (Tunnelblick VPN Configurations are available only on Tunnelblick 3.1 and up.)
  * **OpenVPN configuration files.** These are plain text files with extensions of .ovpn or .conf. These files usually contain only the configuration information; keys and certificates are held in separate files. **For more information about setting up Tunnelblick using OpenVPN configuration files, see [Configuring OpenVPN](cConfigO.md).**

Tunnelblick VPN Configurations may also contain other information, including information about default preferences for the configuration and identification and version information for the configuration itself that make managing widespread distribution easier. For details, see [Tunnelblick VPN Configurations Details](cPkgs.md).

## Converting OpenVPN Configurations to Tunnelblick VPN Configurations ##
Tunnelblick version 3.3beta22 and higher can convert OpenVPN configurations to Tunnelblick VPN Configurations. This is primarily used to transition to newer versions of Tunnelblick. When you launch Tunnelblick and have private OpenVPN configurations, Tunnelblick will offer to convert them to Tunnelblick VPN Configurations. Two important points:
  * The OpenVPN configurations must be "valid" -- that is, any key and certificate files that are referenced must exist; and
  * Any OpenVPN configurations that are not converted are not available for use.

(You can also double-click an OpenVPN configuration and it will be installed as a Tunnelblick VPN Configuration.)

## Creating and Installing a Tunnelblick VPN Configuration ##
To create a Tunnelblick VPN Configuration:

  1. Create a folder anywhere (on your Desktop works well);
  1. If you have only one OpenVPN configuration file, name the folder with the name you want the configuration known by in Tunnelblick. (Otherwise, each configuration will be known in Tunnelblick by the name of the OpenVPN configuration file that it uses);
  1. Copy all the files related to the configuration(s) into the folder (see [Files Contained in a Tunnelblick VPN Configuration](#Files_Contained_in_a_Tunnelblick_VPN_Configuration.md), below);
  1. Add an extension of ".tblk" at the end of the folder name. When you do this the icon for folder will change into a Tunnelblick VPN Configuration.
  1. Double-click the folder's new icon to install it.

When you double-click it, you will be asked if you want each configuration to be private or shared. A private configuration may only be used when you are logged onto the computer. A shared configuration may be used by anyone who is logged into the computer. If the name you have given conflicts with the name of an existing installed configuration, you will be given the opportunity to change the name.

The process of installation will copy the .tblk to a special location on your computer (see  [File Locations](cFileLocations.md)) and make changes to it so it can be used securely. You can then delete the original .tblk you created, or move it somewhere convenient as a backup, or copy or move it to another computer and double-click it on that computer to install it. (The Tunnelblick program must be installed on any computer before you double-click a .tblk on that computer.)

That's it! You are done. The configuration(s) will be available immediately in Tunnelblick.

## Modifying a Tunnelblick VPN Configuration ##
You can modify a Tunnelblick VPN Configuration two ways:
  * If you want to change the contents of the installed OpenVPN configuration file, you should select the configuration in Tunnelblick's VPN Details… window, then click the "gear" button at the bottom of the list and select "Edit OpenVPN Configuration File…". That will open the installed OpenVPN configuration file in TextEdit. Changes take effect as soon as the file is saved in TextEdit. Note that this does not modify your original .tblk; it modifies the installed copy only.
  * If you want to make other changes (to the key/certificate files, for example), you'll have to
    1. Modify your original .tblk to include the changes (rename it to not end in ".tblk", then make the changes, then rename it to end in ".tblk" again);
    1. Delete the old configuration (select the configuration in Tunnelblick's VPN Details… window, then click the "-" button at the bottom of the list); and
    1. Install the modified .tblk by double-clicking it.

## Files Contained in a Tunnelblick VPN Configuration ##
The files that should be contained in a Tunnelblick VPN Configuration (the "files related to the connection" in 3. above) should all be "plain text" files:
  * One or more OpenVPN configuration files (.ovpn or .conf files).
  * Any certificate or key files for the configurations (.key, .crt, .pem, .cer, .der, .p12, .p7b, .p7c, and .pfx files); and
  * Any script files for the configurations. Script files must must have a .sh extension so that Tunnelblick can secure them and use them properly.

## The "Set Nameserver" Check Box and DNS & WINS Settings ##
If you are using DHCP, wish to use DNS and WINS servers at the far end of the tunnel when connected, and the VPN server you are connecting to "pushes" DNS and WINS settings to your client, select "Set nameserver". (This is the situation for most users.)

If you are using DHCP, wish to use your original DNS and WINS servers when connected, and the VPN server you are connecting to does not "push" DNS or WINS settings to your client, select "Do not set nameserver".

If you are using manual settings, different versions of OS X behave differently. This is due to a change in network behavior in Snow Leopard and is beyond the scope of this project to fix.

  * If you're using Leopard (10.5) or Tiger (10.4), then it is possible to use the VPN-server-supplied DNS and WINS settings **in addition to** your manual settings by selecting "Set nameserver". However, your manual settings will always take precedence over any VPN server-supplied settings.  If "Do not set nameserver" is selected, you will continue to use only your manually-configured settings and any VPN server-supplied settings will be ignored. "Take precedence" means that the manual DNS server will be used for all DNS queries unless it fails to answer, in which case the VPN server-supplied DNS server will be used.

  * f you are using Snow Leopard (10.6), then your usual DNS and WINS settings will **always** be used, and no aggregation of configurations will be performed.

  * If you set your DNS servers manually, then regardless of the state of "Set nameserver", your manual DNS servers will always be the only ones used.

  * If you set your Search Domain(s) manually, then regardless of the state of "Set nameserver", your manual Search Domains will always be the only ones used.

  * If you set your WINS servers manually, then regardless of the state of "Set nameserver", your manual WINS servers will always be the only ones used.

  * Each of these settings is independent of the others: if "Set nameserver" is selected, those settings not configured manually will be replaced by the settings obtained from the VPN server.  If "Do not set nameserver" is selected, then as with Leopard/Tiger, no DNS/WINS settings will be applied.

**If your situation is not described above** (e.g., if you use manual DNS settings and wish to use DNS servers at the far end of a tunnel when connected, or you wish to use the OS X ability to use different nameservers for different domains), you must create your own up/down scripts and select "Set nameserver".

## The OpenVPN --user and --group options and openvpn-down-root.so ##
When using "Set nameserver" or your own down script for OpenVPN, it is usually necessary to avoid using the OpenVPN "user" and "group" options in the configuration file. These options cause OpenVPN to drop root privileges and take the privileges of the specified user and group (usually, "nobody"). If this is done, then the down script that handles restarting connections when there is a transient problem fails, because it is run without root privileges. Restoring routes when a tunnel is disconnected fails, also.

However, Tunnelblick includes the "openvpn-down-root.so" plugin for OpenVPN. When this plugin is activated, OpenVPN still drops root privileges and runs as the specified user:group after a connection is made, but runs the down script run as root:wheel, so reconnecting after transient network problems works.

When you try to connect with a configuration that includes the "user" and/or "group" options in the configuration file. Tunnelblick will ask if you wish to use the openvpn-down-root plugin. Answer in the affirmative and Tunnelblick will use the plugin each time it makes a connection. OpenVPN will still be unable to make route changes after the initial connection; they have to be made in the scripts.

## When and How to NOT Use a Tunnelblick VPN Configuration ##
Although Tunnelblick VPN Configurations are able to be shared and connected when your computer starts, they are only available on the latest versions of Tunnelblick (starting with Tunnelblick 3.1beta02). If you are using an older version of Tunnelblick or distributing a configuration to users of older versions of Tunnelblick, you must use only the OpenVPN configuration file (.ovpn or .conf extension). It must be located in

> ~/Library/Application Support/Tunnelblick/Configurations

which, for user "angelolaub", would be located at

> /Users/angelolaub/Library/Application Support/Tunnelblick/Configurations

You may put your certificate, key, and script files in that folder also.

Note that only the OpenVPN configuration file will be secured.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###