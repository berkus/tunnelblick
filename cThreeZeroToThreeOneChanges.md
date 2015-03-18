## Summary of Major Changes from Version 3.0 to Version 3.1 ##
  * A new kind of configuration, a 'Tunnelblick VPN Configuration', includes all information needed to make a connection (OpenVPN configuration file, certificates, keys, scripts, etc.)
    * They may be shared among all users of a computer, or they may be private to a particular user.
    * They can be connected automatically when the computer starts. Tunnelblick can disconnect and connect (i.e., stop and start) them, and they will stay connected when Tunnelblick quits.

  * Loads and unloads tun and tap kexts only as needed.

  * Includes OpenVPN 2.1.4.

  * Includes imbedded OpenSSL 1.0.0c, which contains fixes for security vulnerabilities and adds support for many more digests and ciphers. Thanks to Mohammad A. Haque!

  * Improved display when there are a large number of configurations.

  * Replaces the 'Set nameserver' checkbox with a drop-down list that displays additional choices.

  * Scripts may be run before a tunnel is connected and/or after it is disconnected, providing more flexibility for complex or mixed VPN situations.

  * Deployers can easily add menu items to the Tunnelblick menu to execute programs (e.g., scripts).

  * Deployers can specify programs that should be executed when Tunnelblick is launched or before a connection is attempted.

  * Benji Greig has created an updated Tunnelblick icon that looks great in Coverflow. He has also created a distinctive icon for Tunnelblick VPN Configurations, and a new background image for the Disk Image. Thanks, Benji!

  * Many thanks also to Michael Williams. Several new enhancements are possible due to the his work.

  * Implements a single, system-wide shortcut key to expose the Tunnelblick menu.

  * The DNS cache is now flushed after the tunnel is established and after it is torn down. This is enabled by default but may be disabled by the per-connection "-doNotFlushCache" preference.

  * Includes localization-related code tweaks by Stefan Bethke.

  * Includes Polish localization by Grzegorz Danecki and Italian localization by Pierpaolo Gulla.

  * A DHCP renew which restores the original DNS and/or WINS information no longer causes the connection to restart.

  * The documentation has been reorganized and expanded.


---

## Details of Changes from Version 3.0 to Version 3.1 ##
  * Polish localization by Grzegorz Danecki. Dziękuję bardzo!
  * Italian localization by Pierpaolo Gulla. Grazie!
  * Additional Norwegian Bokmål localization by Jon Luberth. Tusen takk!
  * Additional French localisation by François Varas. Merci beaucoup!
  * Additional Catalan localization by Aleix Dorca. Moltes gràcies!
  * Additional German localization by by Stefan Bethke, Marcus Schneider, and 'Dr Hok'. Vielen Dank!

  * Configurations may now be shared among all users of a computer, or they may be private to a particular user.
    * A new button in the 'VPN Details…' window makes changing the availability of a configuration easy. The button displays either 'Share configuration' or 'Make configuration private', as appropriate.
    * To be shared, a configuration must be a 'Tunnelblick VPN Configuration'.
    * The Shared folder (/Library/Application Support/Tunnelblick/Shared) and its contents are protected. It is owned by root and may only be modified by administrators.
    * Shared configurations (like deployed configurations) may only be examined, not edited. (But you can make it private, edit it, and then share it).
    * Shared configurations are indicated by '(Shared)' after their names in the Tunnelblick menu and in the title of the OpenVPN Log window, and private configurations are indicated by '(Private). If there are also deployed configurations, they are indicated by '(Deployed)' after their names.
    * You can use private and/or shared configurations with Deployed configurations. This is NOT DONE UNLESS a preference named 'useLibraryConfigurationsWithDeployedOnes' and/or 'useSharedConfigurationsWithDeployedOnes' (boolean) is forced TRUE in the 'forced-preference.plist' file.
    * If a deployed configuration and/or a shared configuration and/or a normal configuration ( in ~/Library/Application Support/Tunnelblick/Configurations) have the same names, the deployed one will be displayed if it exists, otherwise the shared one will be displayed if it exists, and the other(s) will be hidden and unavailable. A warning will be issued to notify the user if any configurations are hidden.

  * A new kind of configuration, a 'Tunnelblick VPN Configuration', may be used and may be shared among all users of a computer, or remain private to an individual user (see http://code.google.com/p/tunnelblick/wiki/PackagesProposal for details):
    * A Tunnelblick VPN Configuration is an OS X folder with an extension of '.tblk'.
    * A Tunnelblick VPN Configuration includes one .ovpn configuration file, and many include key and certificate files and shell scripts. It can also include default settings for per-configuration preferences and version information to help manage enterprise distribution of configurations.
    * Tunnelblick VPN Configurations must be installed before they can be used. They can be installed by double-clicking them, or dragging and dropping them on a Tunnelblick icon in Finder (but not the Tunnelblick icon in the Status Bar near the Spotlight icon). They can also be automatically installed when installing Tunnelblick by including them in the disk image. The user is given the option of installing them as private or shared. All of this behavior can be controlled and/or inhibited by preferences, which can be 'forced' in a Deployed version of Tunnelblick.
    * Tunnelblick VPN Configurations and their contents are secured. Key and certificate files, for example, may not be read by the user. (The protection is not as robust as that for Deployed configurations, so that users may edit the configuration, but they are secure in the sense that a user is never allowed to use a configuration that has not been authorized by a computer administrator.)

  * Tunnelblick can now start Tunnelblick VPN Connections (clients or servers) when the computer starts:
    * A new option in the Details window is available for Shared and Deployed .tblk packages: to connect automatically 'when the computer starts'.
    * When Tunnelblick is launched, it attaches itself to any OpenVPN processes which were started because of that option and allows control (disconnect/connect) of them, and displays their logs.
    * When Tunnelblick quits, it closes only those connections which do not have 'when computer starts' selected. Thus OpenVPN instances started outside of Tunnelblick will continue, as will those started by Tunnelblick at any time that have 'when computer starts' selected at the time Tunnelblick quits.
    * If any unknown OpenVPN processes are running a few seconds after Tunnelblick is launched (i.e., after it has 'hooked up' to ones it started because of the 'when the computer starts' option), it pops up a window which gives the user the option to terminate them or ignore them. A checkbox in the window allows the user to 'Do not display this message again, always ignore'. There is a preference, 'hookupTimeout' that is the number of seconds to try, with a default of five seconds.
    * Note that these 'when the computer starts' configurations must not ask for usernames, passwords, or private keys. (There is no user to ask, and no Tunnelblick to pull them out of the Keychain and give to OpenVPN.)

  * Tunnelblick now deals with the .tun and .tap kexts more flexibly:
    * Scans the configuration file to determine if 'tap' or 'tun' is being used, and loads only the appropriate kext at connect. (Tunnelblick uses the argument to the first 'dev-type' if it appears, otherwise it uses whatever is specified in the first 'dev' option in the configuration file.)
    * Loads and unloads them on demand: loaded at connect, unloaded at disconnect. A load is ignored if the kext is already loaded and an unload is ignored if the kext is in use.
    * foo.tun and foo.tap are unloaded only as needed to make a connection: foo.tap is unloaded if net.tunnelblick.tap is being loaded for the connection, and foo.tun is unloaded if net.tunnelblick.tun is being loaded for the connection. The 'skipAskingToUnloadFooKexts' preference is no longer used.
    * New per-configuration preferences can be used to override the automatic detection of which kexts to load at connect: -loadTapKext, -loadTunKext, -doNotLoadTapKext, and -doNotLoadTunKext are all to be prefixed by the configuration name. (If both 'load…' and 'doNotLoad…' preferences exist for a specific configuration, the specified kext will not be loaded.)

  * Two new scripts, pre-connect.sh and post-disconnect.sh, may be in a Tunnelblick VPN Configuration (.tblk). If present, they are executed before connecting and/or after disconnecting, respectively. This allows easy manipulation of kexts and/or the network configuration before the tun/tap kexts are loaded and OpenVPN is run and after OpenVPN exits and the kexts are unloaded.

  * Log processing and display have been rewritten:
    * OpenVPN log files are kept in /tmp/tunnelblick/logs using filenames encoded with the configuration file path, the management port number, and the arguments to openvpnstart when the connection was created.
    * Script log files are kept in the same directory, using filenames encoded with the configuration file path.
    * Log files are created each time a connection is made. 'Pipes' are no longer used for the script files, and the OpenVPN management interface is not used to process log data.
    * When displaying the log, the entries are merged such that script log entries follow OpenVPN log entries that have the same date/time.
    * The log display now shows the most recent 10000 entries. Earlier entries are not displayed, but they are available in the log files stored in /tmp/tunnelblick/logs.
    * The log display in the VPN Details… window is now read-only from the keyboard.
    * Formatting of the log display is improved.

  * Script processing has been modified:
    * client.up.osx.s and client.nomonitor.up.osx.sh are replaced by client.up.tunnelblick.sh
    * client.down.osx.s and client.nomonitor.down.osx.sh are replaced by client.down.tunnelblick.sh
    * The up and down scripts may be called with optional arguments (before the standard OpenVPN-supplied arguments) that are prefixed by a "-". The arguments are:
      * -m to monitor the network configuration (reflects the 'Monitor connection' checkbox);
      * -w to cause restoration of expected WINS configuration if it changes to the pre-VPN configuration (via DHCP renewal, for example); and
      * -d to cause restoration of expected  DNS configuration if it changes to the pre-VPN configuration (via DHCP renewal, for example).
    * The up script saves, and leasewatch and the down script access, additional parameters (the state of the optional arguments, network primary service ID, and logfile path) in the System Configuration database as /Network/OpenVPN/...
    * The up script saves the pre-VPN WINS (SMB) configuration in the System Configuration database as /Network/OpenVPN/OldSMB
    * The down script ignores the optional arguments (accessing any it needs via the System Configuration database)
    * leasewatch behavior has changed, although a Tunnelblick preference restores the old behavior. It used to restart the connection if the DNS or WINS configuration changed from the post-VPN-creation configuration (which reflects 'pushed' values from the OpenVPN server). This caused a restart of the connection when a DHCP renewal changed the settings to the pre-VPN configuration. This situation is now detected, and the DNS and/or WINS configurations are restored to the post-VPN-creation configuration instead of restarting the connection. This new behavior may be inhibited (forcing the old behavior to restart the connection) by setting the boolean Tunnelblick preferences '-doNotRestoreOnDnsReset' and/or '-doNotRestoreOnWinsReset' to FALSE.

  * Replaces the 'Set nameserver' checkbox with a drop-down list that can display additional choices to allow different up/down scripts to be used.
    * The following choices will always be displayed:
      * 'Do not set nameserver' to not use any scripts                  (equivalent to not having a check in the old 'Set nameserver' checkbox')
      * 'Set nameserver'        to use the standard Tunnelblick scripts (equivalent to having a check in the old 'Set nameserver' checkbox')
    * The following two additional choices will be displayed only if custom scripts are not being used:
      * 'Set nameserver (3.0b10)'      to use scripts from Tunnelblick 3.0b10 for backward compatibility
      * 'Set nameserver (alternate 1)' to use scripts based on Ben Low's scripts from http://openvpn.net/archive/openvpn-users/2006-10/msg00120.html. These scripts:
        * Implements multiple domains 'pushed' from the server
        * Fixes some issues with some TAP connections that cause 'write to TUN/TAP : Input/output error (code=5)' and other errors
        * Does not implement 'Monitor connection'
    * Note: Deployed versions of Tunnelblick and Tunnelblick VPN configurations may include custom scripts that will inhibit the display of these two additional choices.
    * Running this version changes the 'useDNS' per-configuration preference from a boolean to a number. This is a downward-compatible change -- earlier versions of Tunnelblick may be run after running this version and modifying the 'Set nameserver' selection. The earlier version will consider anything other than 'Do not set nameserver' as if the 'Set nameserver' checkbox were checked.
    * Warning: If Build 2054 changes the setting to 'Set nameserver (3.0b10)' or 'Set nameserver (alternate 1)', using an earlier version of Tunnelblick to modify the checkbox so it is checked will revert the setting back to 'Set nameserver'.

  * Implements a single, system-wide keyboard shortcut (command-option-F1 by default) to expose the Tunnelblick menu.
    * This make it possible to use Tunnelblick with only a keyboard.
    * The shortcut key may be used whenever Tunnelblick is running - it does not need to be the front-most application.
    * A new submenu of the Options submenu has been added to allow the key to be use any of the function keys from F1 through F12. The display of the new menu item is inhibited if the 'doNotShowShortcutKeySubmenu' preference is set to TRUE.
    * Two new unsigned integer preferences: 'keyboardShortcutKeyCode' contains the virtual keycode for the key, and 'keyboardShortcutModifiers' contains the code for the modifier keys.

  * Adds ability to add menu items to the Tunnelblick menu to execute programs (e.g., scripts). This includes the ability to specify programs that should be executed when Tunnelblick is launched or when a connection is attempted.  (See http://code.google.com/p/tunnelblick/wiki/cCusDeployed#Additional_Menu_Commands_and_Programs for details.)

  * Streamlines installation to have only one dialog box explaining what will be installed and asking for admin username/password.

  * Tunnelblick now searches for the folder containing animation icons in Tunnelblick.app/Contents/Resources/Deploy and then in /Library/Application Support/Tunnelblick/Shared before defaulting to the built-in version in Tunnelblick.app/Contents/Resources.

  * No longer displays Tooltips by default. They are displayed only if the 'showTooltips' preference is set to TRUE. This is necessary because tooltips on menu items interfere with the proper operation of VoiceOver, OS X's built-in screen access solution.

  * A DHCP renew which restores the original DNS and/or WINS information no longer causes the connection to restart. This new behavior can reversed be by setting Tunnelblick the boolean preferences '-doNotRestoreOnDnsReset' and/or '-doNotRestoreOnWinsReset' to TRUE.

  * When there are no configurations present, two menu items are displayed in place of the configurations:  'No VPN Configurations Available' and 'Add a Configuration…'. (The 'Add a Configuration…' menu item will not be displayed if the 'doNotShowAddConfigurationMenuItem' preference is true.)

  * An 'Add a Configuration…' menu item was added to the 'Options…' submenu. (It will not be displayed if the 'doNotShowAddConfigurationMenuItem' preference is true.)

  * The 'wizard' that runs when there are no configurations present, or when the user selects 'Add a configuration…' has been enhanced.

  * Flushes the DNS cache after a tunnel is established and after it is torn down. Enabled by default; disabled by the per-connection "-doNotFlushCache" preference.

  * The documentation has been reorganized and expanded.

  * The 'Edit Configuration' button becomes 'Examine Configuration' when the configuration may not be edited, i.e., it is a Deployed or Shared configurations.

  * Editing a configuration file requires it to be unprotected first, even on Snow Leopard.

  * Configurations are now listed in case-INsensitive alphabetic order and are no longer surrounded by single-quote marks on the drop-down menu.

  * Configurations (.conf, .ovpn, and .tblk) may be stored in subfolders. Note that .tblk configurations are installed at the top level of the shared or private folder; they must then be moved to a subfolder if that is desired.

  * After unprotecting a configuration file, the previous version (which is still protected) is available as xxx-previous. (If a non-administrator accidentally or mistakenly unprotects a configuration they will still be able to connect by using the xxx-previous version.)

  * The full path of the configuration file is displayed as a tooltip for connection names in the Tunnelblick menu.

  * Tunnelblick now detects if it is located on a volume which doesn't support suid (thumb drives and network volumes, for example). In that circumstance, Tunnelblick offers to install itself to /Applications on the boot volume (the same way it does when Tunnelblick.app is located on a disk image). Note that although Tunnelblick cannot run from such a volume, configurations can reside on such a volume, or even on a volume that does not support root ownership of files, such as a network volume or a volume formatted as FAT32. Configurations on such a volume will be 'shadow copied' to the boot volume before being used. This is done automatically for network volumes, and will be done for non-network volumes if the 'useShadowConfigurationFiles' preference is true.

  * openvpnstart puts a warning in the OpenVPN log (in the VPN Details… window) if the path to the up or down script is very long, which could result in OpenVPN sending incomplete arguments to the scripts. (OpenVPN truncates the command line it uses to start the scripts to 255 characters.)"

  * Warnings from openvpnstart program are now included in the OpenVPN log displayed in the 'VPN Details…' window.

  * Warning issued if up/down script paths may be too long for OpenVPN to deal with.

  * Changed title of 'OpenVPN Log - Tunnelblick' window to 'Details - Tunnelblick'.

  * Removed extra Console Log message that the program needed repair.

  * Logs errors trying to create or update 'Launch Tunnelblick' in the private configurations folder.

  * Fix omission and improve formatting of openvpnstart command line tool.

  * Attempts to repair more configuration folder problems, such as the existence of both the old and new folders.

  * Tries up to five times to get the login items, avoiding a timing issue.

  * Works around the following OpenVPN bug: when in the 'RESOLVE' state, the OpenVPN process ignores the first SIGTERM (via kill or management interface) and to delays termination for tens of seconds after the second SIGTERM. Works around this by warning the user that this is happening, then repeatedly sending SIGTERM and, after a timeout period (default is 180 seconds), considering the connection closed even if OpenVPN doesn't acknowledge the closing. Two new preferences specify the time in seconds between sending SIGTERMs ('openvpnTerminationInterval') and the total maximum time to wait before considering the connection closed ('openvpnTerminationTimeout').

  * Fixed bug that sometimes ignored the 'updateSendProfileInfo' preference.

  * Fixed bug that sometimes send partial anonymous profile information when checking for updates.

  * Fixed bug that caused wildcard matches of forced preferences to always fail.

  * Fixed bug that allowed setting of user preferences for forced preferences (although they are then ignored).

  * Fixed bug that caused incorrect permissions (644) to be set on subfolders of Tunnelblick.app/Contents/Resources/Deploy, making them inaccessible. If an existing deployed version of Tunnelblick has such subfolders, the permissions of subfolders will be corrected (to be 755) at first launch after updating Tunnelblick.

  * Fixed bug that sometimes created and used shadow copies of Deployed configurations.

  * Fixed bug that caused unnecessary check of ownership/permissions of Tunnelblick.app/Contents/Resources/Deploy.

  * Fixed bugs (race conditions) when the log view is being updated and when MenuExtras are added.

  * Fixed a formatting error when displaying file permissions in error messages about being unable to change permissions.

  * Fixed a problem causing a connection restart when 'Set nameserver' is used, a DHCP renewal occurs, and there are no WINS settings.

  * Fixed issues when using OpenDirectory and the user's home directory is on a non-Mac platform.

  * Fixed bug that caused an unneeded folder (dmgFiles) to be built into Tunnelblick.app/Contents/Resources.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS