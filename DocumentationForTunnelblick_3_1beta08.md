

&lt;hr&gt;


<font size='3'><b><a href='http://tunnelblick.googlecode.com/files/Tunnelblick_3.1beta08.dmg'>Download Tunnelblick 3.1beta08</a></b></font>


&lt;hr&gt;



**[Full Release Notes](RlsNotes.md)**

## What's New in Tunnelblick 3.1beta08 (Changes from 3.1beta06) ##
  * <font color='red'><b>IMPORTANT NOTE FOR THOSE USING "WHEN COMPUTER STARTS" WITH EARLIER BETA VERSIONS:</b></font> When you update to Tunnelblick 3.1beta08 or above from 3.1beta02 - 3.1beta06, Tunnelblick will not recognize any **running** "when computer starts" configurations. Five to ten seconds after you start Tunnelblick, they will be identified as unknown OpenVPN processes and you will be given the choice to leave them alone or disconnect them. You should chose to disconnect them in this dialog and then manually connect them in Tunnelblick. (You do not need to do this immediately, but you will not be able to control them with Tunnelblick. The dialog will appear each time you start Tunnelblick if these connections are still active.) This need only be done once, and is not necessary if there are no "when computer starts" configurations that are connected at the time you update.

  * Benji Greig has created an updated Tunnelblick icon that looks great in Coverflow. He has also created a distinctive icon for Tunnelblick VPN Configurations, and a new background image for the Disk Image. Thanks, Benji!

  * Log processing and display have been rewritten:
    * OpenVPN log files are kept in /tmp/tunnelblick/logs using filenames encoded with the configuration file path, the management port number, and the arguments to openvpnstart when the connection was created.
    * Script log files are kept in the same directory, using filenames encoded with the configuration file path.
    * Log files are created each time a connection is made. 'Pipes' are no longer used for the script files, and the OpenVPN management interface is not used to process log data.
    * When displaying the log, the entries are merged such that script log entries follow OpenVPN log entries that have the same date/time.
    * The log display now shows the most recent 10000 entries. Earlier entries are not displayed, but are in the log files stored in /tmp/tunnelblick/logs.
    * Formatting of the log display is improved.

  * The DNS cache is flushed after a tunnel is established and after it is torn down. This is enabled by default but may be disabled by the per-connection "-doNotFlushCache" preference.

  * Tunnelblick VPN Configurations (.tblk packages) may now be shadow copied.

  * Configurations (.conf, .ovpn, and .tblk) may be stored in subfolders. Note that .tblk configurations are installed at the top level of the shared or private folder; they must then be moved to a subfolder if that is desired.

  * Sets share/private button to 'Share configuration' when it is disabled.

  * Fixes bug that caused 'Ignoring change of Network Primary Service' message to be displayed when no change occurred.

  * Fixes bug that caused unload of tun/tap kext at exactly the right time while a restart was taking place if the user disconnected a different configuration that used the same tun/tap kext.

  * Fixes bug that caused .conf configuration files to be ignored.

  * Fixes bug that caused failure to connect if "Monitor connection" was checked and the standard up script was used.

  * Fixes bug that caused restarts to fail if a different configuration was disconnected at exactly the right (or wrong!) time.

  * Fixes bug that didn't clean up when installation of a .tblk package failed.

  * Fixes bug that caused 'Set nameserver' script (i.e., 'leasewatch') to be run when it is not necessary.

  * Fixes bug that caused launch of leasewatch script (when 'Set nameserver' is checked) to fail if automatically connecting when computer starts

  * Fixes bug which causes format errors in the log display if a script generates log entries which don't have a "`*`" after the date/time. (Inserts a "`*`" in such entries in the log display.)


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS