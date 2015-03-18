## What's New in Tunnelblick 3.1beta02 ##
  * Norwegian Bokmål (NB) localization by Jon Luberth. Tusen takk!
  * Polish (PL) localization by Grzegorz Danecki. Dziękuję bardzo!
  * Additional French (FR) localisation by François Varas. Merci beaucoup!
  * Additional Catalàn (CA) localization by Aleix Dorca. Moltes gràcies!

  * Many thanks also to Michael Williams. Many new enhancements are possible due to the his work. He contributed code that allows configurations in more than one folder to be available simultaneously. This has triggered an overhaul of the way Tunnelblick handles configurations, adding many new features.

  * Configurations are now listed in case-INsensitive alphabetic order and are no longer surrounded by single-quote marks on the drop-down menu.

  * Configurations may now be shared among all users of a computer, or they may be private to a particular user.

  * A new button in the 'Details…' window makes changing the availability of a configuration easy. The button displays either 'Share configuration' or 'Make configuration private', as appropriate.

  * To be shared, a configuration must be a 'Tunnelblick VPN Configuration' (see below).

  * The Shared folder (/Library/Application Support/Tunnelblick/Shared) and its contents are protected. It is owned by root and may only be modified by administrators.

  * Shared configurations (like deployed configurations) may only be examined, not edited. (But you can make it private, edit it, and then share it).

  * Adds the ability to start VPN connections (clients or servers) when the computer starts:
    * A new option in the Details window is available for Shared and Deployed .tblk packages: to connect automatically 'when the computer starts'.
    * When Tunnelblick is launched, it attaches itself to any OpenVPN processes which were started because of that option and allows control (disconnect/connect) of them, and displays their logs.
    * When Tunnelblick quits, it closes only those connections which do not have 'when computer starts' selected. Thus OpenVPN instances started outside of Tunnelblick will continue, as will those started by Tunnelblick at any time that have 'when computer starts' selected at the time Tunnelblick quits.
    * If any unknown OpenVPN processes are running a few seconds after Tunnelblick is launched (i.e., after it has 'hooked up' to ones it started because of the 'when the computer starts' option), it pops up a window which gives the user the option to terminate them or ignore them. A checkbox in the window allows the user to 'Do not display this message again, always ignore'. There is a preference, 'hookupTimeout' that is the number of seconds to try, with a default of five seconds.
    * Note that these 'when the computer starts' configurations must not ask for usernames, passwords, or private keys. (There is no user to ask, and no Tunnelblick to pull them out of the Keychain and give to OpenVPN.)

  * A new kind of configuration, a 'Tunnelblick VPN Configuration', may be used and may be shared among all users of a computer, or remain private to an individual user (see PackagesProposal for details):

  * A Tunnelblick VPN Configuration is an OS X folder with an extension of '.tblk'.

  * A Tunnelblick VPN Configuration includes one .ovpn configuration file, and many include key and certificate files and shell scripts. It can also include default settings for per-configuration preferences and version information to help manage enterprise distribution of configurations.

  * Tunnelblick VPN Configurations must be installed before they can be used. They can be installed by double-clicking them, or dragging and dropping them on a Tunnelblick icon in Finder (but not the Tunnelblick icon in the Status Bar near the Spotlight icon). They can also be automatically installed when installing Tunnelblick by including them in the disk image. The user is given the option of installing them as private or shared. All of this behavior can be controlled and/or inhibited by preferences, which can be 'forced' in a Deployed version of Tunnelblick.

  * Tunnelblick VPN Configurations and their contents are secured. Key and certificate files, for example, may not be read by the user. (The protection is not as robust as that for Deployed configurations, so that users may edit the configuration, but they are secure in the sense that a user is never allowed to use a configuration that has not been authorized by a computer administrator.)

  * Deals with the .tun and .tap kexts more flexibly:
    * Loads and unloads them on demand: loaded at connect, unloaded at disconnect. An load is ignored if the kext is already loaded and an unload is ignored if the kext is in use.
    * Scans the configuration file to determine if 'tap' or 'tun' is being used, and loads only the appropriate kext at connect. (Tunnelblick uses whatever is specified in the first 'dev' option in the configuration file.)
    * New per-configuration preferences can be used to override the automatic detection of which kexts to load at connect: -loadTapKext, -loadTunKext, -doNotLoadTapKext, and -doNotLoadTunKext are all to be prefixed by the configuration name. (If both 'load…' and 'doNotLoad…' preferences exist for a specific configuration, the specified kext will not be loaded.)
    * When Tunnelblick launches, it unloads net.tunnelblick.tun and net.tunnelblick.tap so that the versions in use will always be loaded from the running version of Tunnelblick.app. The unload will not occur if the kexts are in use -- for example, by an instance of OpenVPN started when the computer started.
    * If foo.tap and foo.tun are loaded when Tunnelblick launches, it offers to unload them. (They are the old Tunnelblick kexts.) This simplifies the transition to the new net.tunnelblick.tun/tap for most users without a computer restart.

  * You can now allow access to private and/or shared configurations in a Deployed version of Tunnelblick. This is NOT DONE UNLESS a preference named 'useLibraryConfigurationsWithDeployedOnes' and/or 'useSharedConfigurationsWithDeployedOnes' (boolean) is forced TRUE in the 'forced-preference.plist' file.

  * If a deployed configuration and/or a shared configuration and/or a private configuration have the same names, the deployed one will be displayed if it exists, otherwise the shared one will be displayed if it exists, and the other(s) will be hidden and unavailable. A warning will be issued to notify the user if any configurations are hidden.

  * Shared configurations are indicated by '(Shared)' after their names in the Tunnelblick menu and in the title of the "Details…" window, and private configurations are indicated by '(Private). If there are also deployed configurations, they are indicated by '(Deployed)' after their names.

  * The 'Edit Configuration' button becomes 'Examine Configuration' when the configuration may not be edited, i.e., it is a Deployed or Shared configurations.

  * Editing a configuration file requires it to be unprotected first, even on Snow Leopard.

  * After unprotecting a configuration file, the previous version (which is still protected) is available as xxx-previous. (If a non-administrator accidentally or mistakenly unprotects a configuration they will still be able to connect by using the xxx-previous version.)

  * The full path of the configuration file is displayed as a tooltip for connection names in the Tunnelblick menu.

  * Tunnelblick now detects it is located on a volume which doesn't support suid (thumb drives and network volumes, for example). In that circumstance, Tunnelblick offers to install itself to /Applications on the boot volume (the same way it does when Tunnelblick.app is located on a disk image).

  * Note that although Tunnelblick cannot run from such a volume, configurations can reside on such a volume, or even on a volume that does not support root ownership of files, such as a network volume or a volume formatted as FAT32. Configurations on such a volume will be 'shadow copied' to the boot volume before being used. This is done automatically for network volumes, and will be done for non-network volumes if the 'useShadowConfigurationFiles' preference is true.

  * Other additional new preferences: skipWarningUnableToToEstablishOpenVPNLink, and two per-connection preferences: XXXX-disableConnectButton and XXXX-disableDisconnectButton.

  * Changed title of 'OpenVPN Log - Tunnelblick' window to 'Details - Tunnelblick'.

  * Removed extra Console Log message that the program needed repair.

  * Fix omission and improve formatting of openvpnstart command line tool.

  * Deals better with situation of ~/Library/openvpn and /Library/Application Support/Tunnelblick/Configurations being inconsistent.

  * Fixed bug that sometimes ignored the 'updateSendProfileInfo' preference.

  * Fixed bug that sometimes send partial anonymous profile information when checking for updates.

  * Fixed bug that caused incorrect permissions (644) to be set on subfolders of Tunnelblick.app/Contents/Resources/Deploy, making them inaccessible. If an existing deployed version of Tunnelblick has such subfolders, upon update (via the built-in updater or a fresh .dmg) the permissions of subfolders will be corrected (to be 755) at first launch).

  * Fixed bug that sometimes created and used shadow copies of Deployed configurations.

  * Fixed bug that caused unnecessary check of ownership/permissions of Tunnelblick.app/Contents/Resources/Deploy.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS