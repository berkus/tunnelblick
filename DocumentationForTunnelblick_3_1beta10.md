

&lt;hr&gt;


<font size='3'><b><a href='http://tunnelblick.googlecode.com/files/Tunnelblick_3.1beta10.dmg'>Download Tunnelblick 3.1beta10</a></b></font>


&lt;hr&gt;



**[Full Release Notes](RlsNotes.md)**

## What's New in Tunnelblick 3.1beta10 (Changes from 3.1beta08) ##
  * <font color='red'><b>IMPORTANT NOTE FOR THOSE USING "WHEN COMPUTER STARTS" WITH EARLIER BETA VERSIONS:</b></font> The first time that you update to Tunnelblick 3.1beta08 or above from 3.1beta02 - 3.1beta06, Tunnelblick will not recognize any **running** "when computer starts" configurations. Five to ten seconds after you start Tunnelblick, they will be identified as unknown OpenVPN processes and you will be given the choice to leave them alone or disconnect them. You should chose to disconnect them in this dialog and then manually connect them in Tunnelblick. (You do not need to do this immediately, but you will not be able to control them with Tunnelblick. The dialog will appear each time you start Tunnelblick if these connections are still active.) This need only be done once, and is not necessary if there are no "when computer starts" configurations that are connected at the time you update.



  * Configurations located in subfolders are displayed in submenus of the main Tunnelblick menu.

  * The 'wizard' that runs when there are no configurations present or when the user selects 'Add a configuration…' has been enhanced.

  * When there are no configurations available, two menu items are displayed in place of the configurations:  'No VPN Configurations Available' and 'Add a Configuration…'. (The 'Add a Configuration…' menu item will not be displayed if the 'doNotShowAddConfigurationMenuItem' preference is true.)

  * An 'Add a Configuration…' menu item was added to the 'Options…' submenu. (It will not be displayed if the 'doNotShowAddConfigurationMenuItem' preference is true.) This menu item starts the configuration wizard.

  * When a Tunnelblick VPN Configuration (.tblk package) is installed, all Tunnelblick VPN Configurations within it will be installed. If these 'inner' configurations are inside subfolders of the outer .tblk, they will be installed as subfolders of the configurations folders and will appear in submenus of the main Tunnelblick menu.

  * Automatic installation of configurations from the .dmg has changed: Only one Tunnelblick VPN Configuration (.tblk packages) in the '.auto-install' or '.auto-install' folders and their subfolders is installed.

  * The ability to install Tunnelblick VPN Configurations from malformed folder contents has been improved.

  * Tunnelblick now tries up to five times to get the login items, avoiding a timing issue.

  * The log display in the Details… window is now read-only from the keyboard.

  * If it doesn't exist, Tunnelblick creates a symlink to ~/Library/Application Support/Tunnelblick/Configurations from ~/Library/openvpn. This avoids a problem when a user launches a new version of Tunnelblick one or more times without having ever used an older version, and then tries to use an older version.

  * Attempts to repair more configuration folder problems, such as the existence of both the old and new folders.

  * Fixes bugs in the shadow copy mechanism that caused connect failures, log-hookup failures, and (possibly) other problems. Thanks to Jim Bo for pointing out the first problem and suggesting a solution.

  * Fixes bug that caused tun/tap kexts to fail to unload when a connection was closed

  * Fixes incorrect help message for 'openvpnstart'

---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS