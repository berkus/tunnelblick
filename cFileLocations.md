

## The Tunnelblick Application ##
The Tunnelblick application, Tunnelblick.app, is usually stored in /Applications on the startup volume. However, it may be located anywhere on any volume whose filesystem has appropriate security support. In general, that means any local hard drive. For security reasons, Tunnelblick can only run from a volume whose filesystem supports 'suid'. Thus it cannot be run from network drives, external drives including thumb or flash drives, or CD/DVD drives. Any attempt to run Tunnelblick from such a drive will result in an error message and an offer to install Tunnelblick in /Applications on the startup drive.

## OpenVPN, Drivers, and Scripts ##
The OpenVPN program, openvpn-down-root.so, the "tun" and "tap" kext driver files, and standard client up/down scripts are included with, and contained within, Tunnelblick.app.

## Log Files ##
Log files are stored in /Library/Application Support/Tunnelblick/Logs. (Early versions of Tunnelblick stored them in /tmp/tunnelblick). The log files for a configuration are created or deleted and recreated each time the connection is made. There are two log files for each configuration, an OpenVPN log file and a scripts log file. The contents of the files are merged in the display in Tunnelblick's "VPN Details…" window.

## Key and Certificate Files ##
These may be stored anywhere, but typically they are stored in the same folder as the configuration (.ovpn or .conf) file. Key and certificate files associated with a Tunnelblick VPN Configuration (.tblk) are stored inside the configuration itself.

Key and certificate files usually have an extension of .cer, .crt, .der, .key, .p12, .p7b, .p7c, .pem, or .pfx.

## Configuration Files ##
There are two types of configuration files:

  * Tunnelblick VPN Connection files (.tblk files), which include within them one OpenVPN configuration file and all key, certificate, and script files used by the configuration; and

  * OpenVPN configuration files (.ovpn and .conf files). Keys, certificates, and scripts associated with a configuration file are often stored as separate files, but may be included within the configuration file itself.

<font color='red'>Note: Tunnelblick VPN Configurations should always be installed by double-clicking them.</font> If you just move or copy them they may not work properly.

There are five places configuration files may be stored:

  * Private configurations, including both types of files, are stored in '~/Library/Application Support/Tunnelblick/Configurations'. Since these files are all located in the user's Library folder, they must be set up separately for each user. (Note that the "~" in the path indicates the user's home folder; thus the folder is actually located somewhere such as /Users/username/Library/Application Support/Tunnelblick/Configurations. Do not confuse this Library folder with the /Library folder located at the root of the filesystem.)

  * Shared configurations, which can only be Tunnelblick VPN Connection files, are stored in /Library/Application Support/Tunnelblick/Shared. Shared configurations do not need to be set up for each user. (In fact, that's the whole point of sharing them!)

  * [Deployed configurations](cDeployingTunnelblick.md), including both types of files, are stored within the Contents/Resources folder of Tunnelblick.app itself. They do not need to be set up for each user, and are accessible to all users of the computer with access to the application. (To access the internal contents of Tunnelblick.app  in the Finder, control-click Tunnelblick.app in the Applications folder  and click "Show Package Contents”.)

  * "Shadow" copies of configuration files (if they exist) are located in /Library/Application Support Tunnelblick/Users/_username_. See "useShadowConfigurationFiles" in [Preferences](Preferences.md) for details. Shadow copies are created and maintained by Tunnelblick.

  * Backup copies of Deployed configurations are stored in subfolders of /Library/Application Support/Tunnelblick/Backup. These configurations will be restored if a version of Tunnelblick which is not a Deployed version is installed, making it into a Deployed version.

Note: Prior to Tunnelblick version 3.0b24, private configuration files were stored in ~/Library/openvpn. Version 3.0b24 and later versions automatically move that folder to its new location, and replace it with a symbolic link to the new location.

## LaunchDaemons ##
If a configurations are set to connect when the computer starts, it has a .plist file located in /Library/LaunchDaemons. These .plist files are all named starting with "net.tunnelblick.startup."

## Preferences ##
A user's Tunnelblick preferences are contained in `~/Library/Preferences/net.tunnelblick.tunnelblick.plist`.

Note: In Tunnelblick 3.2beta10 and earlier, preferences are stored in `~/Library/Preferences/com.openvpn.tunnelblick.plist`.

Deployed versions of Tunnelblick may contain a "forced-preferences.plist" file within the Tunnelblick application itself. They are used to override the user's normal preferences; see [Deploying Tunnelblick](cDeployingTunnelblick.md) for details.

Tunnelblick VPN Configurations may also include preference defaults, which are used to initialize the user's preferences (which may then be changed by the user).

## One More Thing… ##
Under certain circumstances, Tunnelblick replaces the configuration folder that older versions of Tunnelblick use,
`~/Library/openvpn`
with a symbolic link to the new location of the folder,
`~/Library/Application Support/Tunnelblick/Configurations`