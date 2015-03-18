

&lt;hr&gt;


<font size='3'><b><a href='http://tunnelblick.googlecode.com/files/Tunnelblick_3.1beta04.dmg'>Download Tunnelblick 3.1beta04</a></b></font>


&lt;hr&gt;



## What's New in Tunnelblick 3.1beta04 (from 3.1beta02) ##
  * Creates pipes for script output to "Details…" window on demand instead of when Tunnelblick launches

  * Deletes logs for 'when computer starts' connections when they are disconnected

  * Doesn't un-check 'Connect automatically' if administrator permission to change from 'when Tunnelblick launches' to 'when computer starts' is cancelled, so connect 'when Tunnelblick launches' will remain in effect

  * Allows cancel out of dialog asking if 'openvpn-down-root.so' should be used

  * Marks start and end of OpenVPN log entries from before Tunnelblick was launched

  * Displays a notice if then OpenVPN log entries from before Tunnelblick was launched are more than 10,000,000 bytes long.

  * Includes path of openvpnstart to be used in Console log messages that a configuration will 'connect when computer starts'

  * Reinforces security of openvpnstart -- it now verifies it is protected before doing any operations

  * Reformats dates in OpenVPN log entries from before Tunnelblick was launched to YYYY-MM-DD HH:MM:SS

  * A DHCP renew which restores the original DNS and/or WINS information no longer causes the connection to restart. This new behavior can reversed be by setting Tunnelblick the boolean preferences '-doNotRestoreOnDnsReset' and/or '-doNotRestoreOnWinsReset' to TRUE.

  * Modified the up, down, and leasewatch scripts:
    * client.up.osx.s and client.nomonitor.up.osx.sh are replaced by client.up.tunnelblick.sh
    * client.down.osx.s and client.nomonitor.down.osx.sh are replaced by client.down.tunnelblick.sh
    * The up and down scripts may be called with optional arguments (before the standard OpenVPN-supplied arguments) that are prefixed by a '-'. The arguments are:
      * -m to monitor the network configuration (reflects the 'Monitor connection' checkbox);
      * -w to cause restoration of expected WINS configuration if it changes to the pre-VPN configuration (via DHCP renewal, for example); and
      * -d to cause restoration of expected  DNS configuration if it changes to the pre-VPN configuration (via DHCP renewal, for example).
    * The -w and -d options are specified if the boolean Tunnelblick preferences '-doNotRestoreOnDnsReset' and/or '-doNotRestoreOnWinsReset' are TRUE.
    * The up script saves, and leasewatch and the down script access, additional parameters (the state of the optional arguments, network primary service ID, and logfile path) in the System Configuration database as /Network/OpenVPN/...
    * The up script saves the pre-VPN WINS (SMB) configuration in the System Configuration database as /Network/OpenVPN/OldSMB
    * The down script ignores the optional arguments (accessing any it needs via the System Configuration database)
    * leasewatch behavior has changed, although a Tunnelblick preference restores the old behavior. It used to restart the connection if the DNS or WINS configuration changed from the post-VPN-creation configuration (which reflects 'pushed' values from the OpenVPN server). This caused a restart of the connection when a DHCP renewal changed the settings to the pre-VPN configuration. This situation is now detected, and the DNS and/or WINS configurations are restored to the post-VPN-creation configuration instead of restarting the connection. This new behavior may be inhibited (forcing the old behavior to restart the connection) by setting the boolean Tunnelblick preferences '-doNotRestoreOnDnsReset' and/or '-doNotRestoreOnWinsReset' to FALSE.
    * Tunnelblick itself has been modified to use the new scripts, but only if the old scripts are not present. That means that an automated build process, for example, which replaces client.up.osx.sh with a customized version, will continue to work, because Tunnelblick will see the old script, and use that instead of using the new script (even if the new script is present).
    * The openvpnstart 'bitMask' argument has additional bits that specify options to send to the scripts (as described above)

  * openvpnstart puts a warning in the OpenVPN log (in the Details… window) if the path to the up or down script is very long, which could result in OpenVPN sending incomplete arguments to the scripts. (OpenVPN truncates the command line it uses to start the scripts to 255 characters.)"

  * Warnings from the openvpnstart program are now included in the OpenVPN log displayed in the 'Details…' window

  * Fixes bug that caused load of tap devices to fail when connecting

  * Fixes bug that sometimes caused log file contents not to display

  * Fixes bug that caused output from leasewatch ('Monitor connection' checkbox checked) to be stored in a /tmp file instead of displayed in the OpenVPN Log on the Details... window for Tunnelblick VPN Configurations (.tblk packages)

  * Fixes bug with 'connect on computer start' causing Tunnelblick to ask, in error, to flip the value of the checkbox

  * Fixes bug with 'when Tunnelblick launched' and 'when computer starts' radio buttons

---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS