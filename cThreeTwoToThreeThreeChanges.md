

&lt;hr&gt;



## Changes from Version 3.2 to Version 3.3 ##

For changes from other versions to Tunnelblick 3.3, see the [Tunnelblick 3.3 Release Notes](RlsNotes#Version_3.3.md).

  * Triple-clicking the Tunnelblick icon opens the VPN Details… window, as does relaunching Tunnelblick from a Dock icon or double-clicking the application in a Finder window.

  * On OS X 10.6 ('Snow Leopard') and higher, Tunnelblick now displays configurations in a way that is similar to the 'List View' in a Finder window: contents of folders can be hidden or exposed by clicking on a disclosure triangle next to the folder name. This may be disabled (and the old way of displaying configurations used) by setting the 'doNotShowOutlineViewOfConfigurations' preference to 'TRUE'.

  * Enhances installation of Tunnelblick VPN Configurations with improved error detection and correction.
    * The user can now replace an existing configuration with a new one.
    * Tunnelblick now complains about files referenced in the OpenVPN configuration file that do not exist or are accessed via a path instead of just a filename.
    * Tunnelblick now removes CR characters from script files.
    * TBReplaceIdentical, TBSharePackage, and TBUninstall in an .tblk outer Info.plist will override corresponding entries in nested .tblks.
    * Detects rich text files and files with illegal characters.

  * Adds complete Finnish and Slovak localization and partial Ukrainian and Chinese (traditional) localization

  * Offers to convert OpenVPN configurations to Tunnelblick VPN Configurations. OpenVPN configurations that are NOT converted are NOT AVAILABLE for connection.

  * Adds a new 'Check apparent IP address after connecting' checkbox to the 'Preferences' panel. There is no default; the user is asked if this should be done the first time Tunnelblick is launched.

  * Adds a checkbox to 'Route all traffic through the VPN' on the Advanced settings window. This adds the 'redirect-gateway def1' option to the arguments to OpenVPN. Note that even if is NOT checked, the configuration file may include the option, or the server may push the option.) Default is not checked.

  * Adds the 'Reconnect when computer wakes up from sleep (if connected when computer went to sleep)' checkbox to the 'Advanced' settings panel. Checked by default.

  * Adds a checkbox to 'Reset the primary interface after disconnecting' on the Advanced settings window. This can fix problems caused by configurations that do not restore DNS or routing properly. The reset is done via an 'ifconfig down' followed by an 'ifconfig up' on the primary interface after the configuration is disconnected. Default is not checked.

  * Adds a new checkbox on the 'Advanced' settings page that tells Tunnelblick to add the domain name provided by OpenVPN to the start of the list of search domains. This checkbox is unchecked by default, and is disabled and unchecked unless the DNS/WINS setting is set to 'Set nameserver'. Adding the domain name does not take place if the search domains are manually set.

  * Adds the 'Revert Configuration…' menu command to revert a private configuration to it's last secured (shadow) version.

  * Adds a 'Show when disconnected' checkbox to the 'Notification window' section of the Appearance preferences tab of the 'VPN Details…' window. This is checked by default.

  * Adds a 'Utilities' tab to the VPN Details… window. It includes buttons to:
    * Launch a customized version of OpenVPN's 'easy-rsa' in Terminal. 'easy-rsa' is a collection of command-line scripts for creating certificates and keys.
    * Copy the Console Log to the Clipboard.
    * Quit all OpenVPN processes.

  * Adds the ability to edit a configuration name by clicking on it and editing it directly.

  * Adds the ability to always use the latest version of OpenVPN.

  * Configurations can now share credentials (usernames/passwords and pass phrases) so that the credentials need not be entered separately for each configuration. (This may be set on the 'Advanced' settings window's 'VPN Credentials' tab.)

  * Changes the 'Copy Log to Clipboard' button to the 'Copy Diagnostic Info to Clipboard' button. The info copied to the clipboard includes the configuration file contents, the log contents, and recent Console log output from Tunnelblick and OpenVPN.

  * Allows the Info.plist of a Tunnelblick VPN Configuration to be located either in the .tblk folder directly, or in its "Contents" subfolder.

  * Allows the replacement of a Tunnelblick VPN Configuration that has an Info.plist even if it does not have a CFBundleIdentifier entry.

  * Enhances security by digitally signing Sparkle.framework (signed versions only).

  * Enhances security by making all of the application's contents owned by root.

  * Enhances security by securing the easy-rsa folder and it's contents.

  * Includes OpenVPN 2.3.2 and 2.2.1, OpenSSL 1.0.1e, and LZO 2.06.

  * Includes several changes with respect to notification windows:
    * Notification windows display the total amount of data uploaded and downloaded and recent up and down transfer rates for client connections.
    * When the pointer (mouse) is over the Tunnelblick icon in the menu bar, the notification windows for all configurations that have been active since Tunnelblick was launched are displayed. (This may be changed on the 'Appearances' panel of the 'VPN Details…' window.)
    * Notification windows do not fade away if the pointer is over any notification window (or the Tunnelblick icon, as described above).
    * Notification windows now have separate 'Connect' and 'Disconnect' buttons.

  * New security enhancements allow install and launch of a 'Deployed' version of Tunnelblick only if:
    * It is a 'rebranded' version of Tunnelblick (source code modified to use a different name); and
    * If Info.plist does not have 'tunnelblick.net' in the 'updateFeedURL' forced preference (or in SUFeedURL if there is no 'updateFeedURL' forced preference); and
    * If Info.plist does not have 'net.tunnelblick' in the CFBundleIdentifier; and
    * If all copies of the program include the Deploy folder. Even updates must include the Deploy folder. (Updates did not previously require the Deploy folder because it would be restored from backups maintained by the program. The program no longer maintains such backups.)

  * Fixes a bug that caused notification windows to appear in Mission Control on Lion even though they were closed.

  * Adds the ability to have a 'route-pre-down.tunnelblick.sh' script that is run before closing a connection. Tunnelblick's 'Set Nameserver' setting uses this to release a TAP device's DHCP lease. This feature (and the DHCP lease release) is available only when using OpenVPN 2.3alpha1 or later and only in Tunnelblick VPN Configurations.

  * Adds two AppleScript nouns for configurations: 'bytesIn' and 'bytesOut' report bytes in or out through a client connection since Tunnelblick was launched.

  * Does not try to connect if the OpenVPN log file could not be created.

  * Adds more specific error messages when files with unrecognized extensions or folders are in a .tblk that is being installed.

  * Does not allow Unicode characters in usernames, passwords, and private keys (OpenVPN does not accept them).

  * Includes more debugging information when OpenVPN starts or fails to start.

  * Warns the user when trying to install a Tunnelblick VPN Configuration (.tblk) into a Deployed version of Tunnelblick that does not allow shared and/or private configurations.

  * Defaults to use the oldest version of OpenVPN available, instead of the newest version.

  * Adds 'Speak' to list of connect/disconnect sounds. If selected, connections and unexpected disconnections will be announced with the system default voice.

  * Adds the 'Check apparent IP address after connecting' checkbox to the 'Preferences' panel. There is no default; the user is asked whether to do this the first time the user launches Tunnelblick.

  * Adds the 'Reconnect when computer wakes up from sleep (if connected when computer went to sleep)' checkbox to the 'Advanced' settings panel. The default is to reconnect.

  * Adds the 'Revert Configuration…' menu command to revert a private configuration to it's last secured (shadow) version.

  * When requesting a computer administrator username/password for installation, Tunnelblick also shows that it will convert OpenVPN configurations to Tunnelblick VPN Configurations if the user has requested the conversion.

  * Adds a subcommand to openvpnstart to revert a configuration to when it was last secured.

  * Does not warn about Tunnelblick being unsigned if Debug build.

  * Accepts multiple 'dhcp-option DOMAIN-SEARCH `<domain>`' options in the configuration file or 'pushed' by the VPN server. If present and search domains were not manually set, they are prepended to any search domains that came from DHCP.

  * Displays clearer error messages when a menu icon set is not found.

  * Displays an error dialog window when a fatal error occurs or if an internal error occurs while trying to check the security of a configuration.

  * No longer checks for unsigned updates.

  * Adds the contents of /etc/resolv.conf to the Tunnelblick log before and after making network configuration changes.

  * Inhibits flush of DNS cache on OS X 10.7 or 10.8 if Hands Off is running.

  * Changes to the maximum log size now take effect immediately.

  * Clarified entry made in Console log when Tunnelblick is shut down because of a Command-Q typed by the user.

  * Keeps a history of Tunnelblick versions that were launched, and displays the most recently used prior version in the log.

  * Adds the 'doNotLaunchOnLogin' preference, which causes Tunnelblick to not launch when the user next logs in, even if Tunnelblick was running when the user logged out. This preference cannot be set in the GUI; to set it type the following into Terminal 'defaults write net.tunnelblick.tunnelblick doNotLaunchOnLogin -bool yes'. To restore normal behavior, type 'defaults write net.tunnelblick.tunnelblick doNotLaunchOnLogin -bool yes'.

  * Fixes a problem that caused configurations in submenus not to be sorted properly.

  * Fixes problems indenting configuration subfolders properly in the VPN Details… window.

  * Fixes a problem in the log display of the command line used to start OpenVPN (cosmetic problem).

  * Fixes a problem causing loss of contents in the log display if the log contains invalid characters.

  * Fixes a problem that caused the Info panel to display an incorrect OpenVPN version if no OpenVPN version was chosen on the Preferences panel.

  * Fixes problems with the log display if the display gets very large.

  * Fixes an invalid link in Sparkle (which implements updates) FR\_CA localization.

  * Fixes problems installing from a disk image.

  * Fixes a problem that disabled the keyboard shortcut (hotkey) until the VPN Details… window was opened.

  * Fixes a problem displaying a shortened log on OS X 10.4 ('Tiger').

  * Fixes a problem that caused Tunnelblick to not create a shadow configuration file when installing a .tblk.

  * Fixes a problem that caused the download statistics shown in the status/notification window to be incorrect.

  * Fixes problems in Tunnelblick's patches to easy-rsa.

  * Fixes a problem that sometimes left horizontal lines on the list of configurations when the list was scrolled up and down.

  * Fixes a problem if a configuration was Deployed and needed to be secured.

  * Fixes a problem that caused the help button on the 'While Connected' tab of the 'Advanced' settings window to do nothing.

  * Fixes several problems running Tunnelblick on OS X 10.4 ('Tiger').

  * Fixes a problem that sometimes caused Tunnelblick installations to fail.

  * Fixes a problem that caused the Tunnelblick icon to not respond to clicks properly after a sleep/wake cycle.

  * Fixes a problem that caused the Tunnelblick icon to disappear when an aborted logout takes place.

  * Fixes a problem that caused reverting a configuration to its last secure shadow copy to fail.

  * Fixes a problem that caused a spurious warning if Tunnelblick was Quit by Activity Monitor or reinstallation.

  * Fixes warnings about unknown preferences.

  * Fixes a problem that caused fatal errors in the down script if a '-useDownRootPlugin'preference was set for the configuration but no 'user nobody' or 'group nobody' options were in the configuration file.

  * Fixes a problem that allowed the user to resize the VPN Details… window when a panel other than 'Configurations' is being displayed on OS X 10.7 ('Lion') and higher.

  * Fixes a problem that didn't repair invalid ownership of /Library/Application Support/Tunnelblick/Users if the ownership was modified by the user.

  * Fixes a problem when the installer fails when trying to connect an unsecured configuration. (This would only happen if something is drastically wrong with the system, such as incorrect ownership or permissions on /Library).

  * Fixes a potential security issue when installing .tblks.

  * Fixes a problem that could cause double-freeing of memory.

  * Fixes a problem that sometimes caused an incorrect display of the settings of a Tunnelblick VPN Configuration that had been replaced.

  * Fixes a problem that caused an unnecessary dialog window to appear when canceling the installation of a Tunnelblick VPN Configuration.

  * Fixes a problem that caused overwritten or truncated text in the status window, the 'Advanced' window, and the Log tab of the 'VPN Details…' window in some languages.

  * Fixes a problem in status window that displays the 'In:' and 'Out:' text incorrectly in languages other than English.



---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS