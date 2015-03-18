<h2>Using Scripts</h2>



<font color='red'>Most Tunnelblick users do not need to use the information on this page; Tunnelblick uses scripts automatically.</font>

**All scripts are run as root** so they can make network configuration changes; thus caution is advised when modifying these scripts or using customized scripts.

This document is about the scripts that Tunnelblick uses. Tunnelblick itself may be accessed from AppleScripts; see [AppleScript Support](cAppleScriptSupport.md).

Tunnelblick uses four types of scripts: Tunnelblick VPN Configuration scripts, OpenVPN scripts, the leasewatch script, and executable files (which may be scripts).

## Tunnelblick VPN Configuration scripts ##
Tunnelblick VPN Configuration scripts are shell scripts that are run by Tunnelblick at particular points in the connection process.
  * They are only available in [Tunnelblick VPN Configurations](cConfigT.md) (available in Tunnelblick 3.1beta06 or later).
  * Tunnelblick does not include any of these scripts; see the [Downloads page](DownloadsEntry.md) for user-contributed scripts.
  * They may be used in special circumstances -- for example, to make modifications to the network configuration when a tunnel is active.
  * The scripts are not run unless Tunnelblick is running, which may or may not be the case for 'connect when computer starts' configurations.
  * The scripts are run as "root". (But [environment variables](#Environment_Variables.md) include the actual user's username.)
  * The following scripts may be used (they must have these exact names):
    * **pre-connect.sh** is executed before Tunnelblick would unload and/or load the tun or tap kexts (whether or not any unload or load takes place).
    * **post-tun-tap-load.sh** is executed after Tunnelblick unloads and/or loads the tun or tap kexts (whether or not any unload or load takes place). Thus, the script is executed immediately before starting OpenVPN.
    * **connected.sh** is executed when a configuration connects.
    * **reconnecting.sh** is executed when OpenVPN loses the VPN connection and is trying to reconnect.
    * **post-disconnect.sh** is executed after OpenVPN has closed the connection.

The scripts will be executed automatically if they are included in the Tunnelblick VPN Configuration (".tblk").

## OpenVPN scripts ##
OpenVPN scripts are scripts run by OpenVPN directly.

Tunnelblick tells OpenVPN to run Tunnelblick's up and down scripts if Tunnelblick's "Set DNS/WINS" is set to anything other than "Do not set nameserver".

up- and down- scripts are shell scripts that are run by OpenVPN immediately after connecting, and immediately after disconnecting, respectively.
  * The scripts are run only when a "Set nameserver" option is selected in the configuration's Settings tab.
  * To run the scripts, Tunnelblick passes OpenVPN "--up", "--down" options. This means that any "up" or "down" options specified in the OpenVPN configuration file are ignored. To use your own custom scripts from within the configuration file, select "Do not set nameserver".
  * Tunnelblick includes a standard up script and a standard down script (client.up.tunnelblick.sh and client.down.tunnelblick.sh, respectively) that are used if no other scripts are present. They are located in Tunnelblick.app/Contents/Resources. The scripts save the current DNS configuration and accept "pushed" configurations from the VPN server when the VPN is connected, and restore the DNS configurations when the VPN is disconnected. If "Monitor connection" is checked, the up script sets up to run the leasewatch script when a network configuration change is detected.
  * The up and down scripts may be called with optional arguments (before the standard OpenVPN-supplied arguments) that are prefixed by a '-'. The arguments are:
    * -m to monitor the network configuration (reflects the 'Monitor connection' checkbox);
    * -w to cause restoration of expected WINS configuration if it changes to the pre-VPN configuration (via DHCP renewal, for example); and
    * -d to cause restoration of expected  DNS configuration if it changes to the pre-VPN configuration (via DHCP renewal, for example).
  * The -w and -d options are specified if the boolean Tunnelblick preferences '-doNotRestoreOnDnsReset' and/or '-doNotRestoreOnWinsReset' are TRUE.
  * In a ["Deployed" version](cCusDeployed.md) of Tunnelblick, the standard scripts may be overridden by including "up.tunnelblick.sh" and "down.tunnelblick.sh" scripts in Tunnelblick.app/Contents/Resources/Deploy.
  * The standard scripts and Deployed scripts may be overridden by including "up.tunnelblick.sh", "down.tunnelblick.sh", and "route-pre-down.tunnelblick.sh" scripts in a [Tunnelblick VPN Configuration](cConfigT.md).
  * For backward compatibility, deprecated scripts named "up.sh", "down.sh", "nomonitor.up.sh", "nomonitor.down.sh" will override any other scripts.

## Other Scripts ##
Tunnelblick uses other scripts, too:

**leasewatch** is a script that is run when a VPN is connected, "Monitor connections" is checked for the configuration, and a network configuration change is detected. It ignores the change, restarts the connection, or restores the VPN's DNS and WINS configuration as appropriate. It is located in Tunnelblick.app/Contents/Resources/leasewatch.

**Executable files**, which may be scripts, are files in /Deploy/Menu (see [Deploying  Tunnelblick](cCusDeployed.md)) which are executed when Tunnelblick launches, when a connection is made, or when the user clicks on additional menu commands. See [Additional Menu Commands and Programs](cCusDeployed#Additional_Menu_Commands_and_Programs.md) for details.

## Script Execution Order ##
Tunnelblick VPN Configuration scripts and -up and -down scripts are executed as follows:

  1. USER ASKS for connection (or one is started by 'connect on launch')
  1. pre-connect.sh will run before attempting to make a connection
  1. post-tun-tap-load.sh will run after the tun/tap kext is loaded (or would have been loaded)
  1. up script will run at the end of the connection process
  1. connect.sh will run if/when the connection is successfully made
  1. If OpenVPN detects a problem and attempts to reconnect:
    * reconnect.sh will run
    * If the OpenVPN '--persist-tun' option is not specified, down script will run at the start of the reconnection process
    * If the OpenVPN '--persist-tun' option is not specified, up script wil be run at the end of the reconnection process
  1. connect.sh will run each time (if any) a reconnection attempt is successful
  1. USER ASKS for connection to be terminated (or quits Tunnelblicks and it isn't a 'when computer starts' configuration)
  1. down script is run
  1. post-disconnect.sh will run after disconnecting

Notes:
  * A reconnect attempt does NOT trigger the pre-connect.sh/post-disconnect.sh sequence.
  * The order of execution of the up script and the connected.sh script is undefined.
  * The order of execution of the down script and the post-disconnect.sh script is undefined.
  * The order of execution of the down and up scripts and the reconnecting.sh script is undefined.

## Environment Variables ##
Tunnelblick VPN Configuration scripts inherit the environment variables from Tunnelblick itself. By default (on OS X 10.8 "Mountain Lion"), they are:
```
 SHELL=/bin/bash
 TMPDIR=/var/folders/***
 Apple_PubSub_Socket_Render=/tmp/***
 USER=***
 COMMAND_MODE=unix2003
 SSH_AUTH_SOCK=/tmp/launch-OVkVOl/Listeners
 __CF_USER_TEXT_ENCODING=0x1F5:0:0
 PATH=/usr/bin:/bin:/usr/sbin:/sbin
 PWD=/private/tmp
 SHLVL=1
 HOME=/Users/***
 LOGNAME=***
 DISPLAY=/tmp/***
 _=/usr/bin/env
```
(where "`*``*``*`" indicates information that varies from login to login or user to user.)

OpenVPN scripts have environment variables set up as specified in the [OpenVPN 2.2 man page](https://community.openvpn.net/openvpn/wiki/Openvpn22ManPage) or the [OpenVPN 2.3 man page](https://community.openvpn.net/openvpn/wiki/Openvpn23ManPage).


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS