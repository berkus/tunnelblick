**For help configuring and using Tunnelblick, see [Using Tunnelblick](UsingTunnelblick.md) and the [Tunnelblick Discussion Group](http://groups.google.com/group/tunnelblick-discuss).**

This document contains the following sections:



## Overview ##
Tunnelblick's preferences for a user are stored in `~/Library/Preferences/com.openvpn.tunnelblick.plist`.

If Tunnelblick.app contains a `Contents/Resources/Deploy/forced-preferences.plist` file, then preferences in that file override the corresponding preferences in the `com.openvpn.tunnelblick.plist` file. This overriding is called "forcing" the preference. See [Deploying Tunnelblick](cDeployingTunnelblick.md) for more details.

Note: some preferences are stored as the opposite of the state of the corresponding check box: For example, the **_config-name_-notMonitoringConnection** preference is the opposite of the "Monitor Connection" check box

## Preferences in the "Options…" Submenu ##
Three preferences may be set or cleared by the user via the "Options…" submenu. See **placeIconInStandardPositionInStatusBar** and **doNotMonitorConfigurationFolder** in [Preferences That Control What Tunnelblick Does](Preferences_That_Control_What_Tunnelblick_Does.md) and **updateCheckAutomatically** in [Preferences That Control Updates](Preferences_That_Control_Updates.md)

## Preferences in the ""Details…"" Window ##
Three preferences may be set or cleared by the user via check boxes on the "Details…" window tab for each configuration. See the **autoConnect**, **useDNS**, and **-notMonitoringConnection** preferences in [Per-Configuration\_Preferences Per-Configuration Preferences].


## Modifying Preferences That are Not in the "Options…" Submenu or the "Details…" ##
All other preferences can only be modified by (A) forcing them or (B) modifying them in `~/Library/Preferences/com.openvpn.tunnelblick.plist` using Apple's "Property List Editor.app". “Property List Editor.app” is a small part of the free [Developer Tools](http://developer.apple.com/technology/Xcode.html) available from Apple (a free Apple Developer Connection membership is required). The Developer Tools are a very large (over 900MB download) suite of programs for developing software for Macs. The Developer Tools installs Property List Editor.app in /Developer/Applications/Utilities.

## Preferences That Control What Tunnelblick Does ##
  * **placeIconInStandardPositionInStatusBar** (Boolean): If set, the Tunnelblick icon will be positioned normally, to the left of the other icons at the time Tunnelblick is started. If cleared or not present, the Tunnelblick icon will be placed between the time display and the Spotlight icon. The default is not present.
  * **doNotMonitorConfigurationFolder** (Boolean): If set, Tunnelblick does not monitor the ~/Library/Application Support/Tunnelblick/Configurations folder for changes to configuration files. If cleared or not present, Tunnelblick monitors the folder and reacts appropriately to configuration files that are added or removed. If set, Tunnelblick must be restarted before showing added or removed configurations. The default is not present.
  * **onlyAdminsCanUnprotectConfigurationFiles** (Boolean): If set, the user will be warned that they will only be allowed to examine configuration files when using the "Edit Configuration" button on OS X 10.4 (Tiger) or 10.5 (Leopard) and will be unable to modify them. If cleared or not present, the user will be asked if they wish to unprotect the configuration file before editing it on Tiger or Leopard. On OS X 10.6 (Snow Leopard), this preference is ignored. On Tiger and Leopard, `TextEdit` will be unable to save a modified configuration file that is protected; on Leopard, `TextEdit` will silently unprotect the configuration file if it is saved after being modified. The default is not present.
  * **standardApplicationPath** (String): If present, the absolute path for the folder in which Tunnelblick is to be installed when installing Tunnelblick by double-clicking the icon in a downloaded disk image. If not present or empty, Tunnelblick will be installed in `/Applications`. The string may include a "~", which will be expanded appropriately to allow installation somewhere in the user's home folder. Default is not present.
  * **doNotCreateLaunchTunnelblickLinkinConfigurations** (Boolean): If set, no link will be created. If cleared or not present, Tunnelblick will create a link to itself in the `~/Library/Application Support/Tunnelblick/Configurations` folder each time it is started. The default is to create the link.

## Preferences That Control What The User Sees ##
  * **menuIconSet** (String): If set, specifies the name of the folder of icons that Tunnelblick should use to display the connection status in the status bar (usually, near the Spotlight icon). The default is "TunnelBlick.TBMenuIcons". The folder must be located in Tunnelblick.app/Contents/Resources/IconSets.
  * **doNotShowForcedPreferenceMenuItems** (Boolean): If set, any preferences that are forced will not be displayed on the "Options…" submenu. If cleared or not present, such preferences are shown dimmed, and are disabled. The default is not present.
  * **doNotShowOptionsSubmenu** (Boolean): If set, the "Options…" submenu will not be displayed. If cleared or not present, the submenu will be displayed. The default is not present.
  * **doNotShowCheckForUpdatesNowMenuItem** (Boolean): If set, the "Check for Updates Now" item on the "Options…" submenu will not be displayed. If cleared or not present, the item will be displayed. The default is not present.

## Preferences That Control Updates ##
  * **updateCheckAutomatically** (Boolean): If set, Tunnelblick checks for updates each time it is launched, and periodically thereafter. If cleared or not present, no checking is done. There is no default value; the user is asked if they want to enable automatic updates the first time Tunnelblick is launched and whenever the information that Tunnelblick sends when checking for an update changes (so the user can decide whether or not to include the information).
  * **updateSendProfileInfo** (Boolean): If set, Tunnelblick will send "system profile" information to the Tunnelblick website when checking for updates. If cleared or not present, no such profile information will be sent when checking for updates. There is no default value; when the user is asked if they want to enable automatic updates the first time Tunnelblick is launched and whenever the information the profile information changes, a check box allows the user to set or clear this value.
  * **updateCheckInterval** (String or Number): If set, the number of seconds between automatic checks for updates. If not present or empty, the default time (86,400 seconds = 24 hours) is used. If a time less than 3600 seconds (one hour) is specified, it will be changed to 3600 seconds. The default is not present.
  * **updateFeedURL** (String): If present, the URL to check for updates. If not present or blank, "http://tunenlblick.net/appcast.rss" (for Tunnelblick 3.0b24 and earlier) or "http://tunnelblick.net/updates/update.php" is used. This preference may ONLY be forced; the user's normal preference is ignored for security reasons. The default is not present.
  * **updateAutomatically** (Boolean): If set, when Tunnelblick detects an update it will be downloaded and installed automatically. If cleared or not present, the user will be asked This preference may ONLY be forced; the user's normal preference is ignored because it can be changed at any time by a Sparkle check box. The default is not present.
  * **onlyAdminCanUpdate** (Boolean): If set, update checking will be disabled unless the logged-in user is a member of the "administrator" group. If cleared or not present, update checking will be performed even if the user is not a member of the "administrator" gouger. After an update, an administrator username/password will be required to run Tunnelblick (so the new copy can secure itself). The default is not present.
  * **updateUUID**: This is an anonymous, unique ID string. If updateSendProfileInfo is set, this string is sent to the Tunnelblick update website when checking for updates. It allows the website to count the number of unique Tunnelblick users.

## Preferences That are Set by the User in a Check Box ##
Most of Tunnelblick's warning messages include a "Do not warn about this again" check box. Checking the check box sets the corresponding preference.
  * **skipWarningAboutReprotectingConfigurationFile** (Boolean): If set, Tunnelblick on Snow Leopard will not warn the user that any changes made to a configuration file will require an administrator username/password before the changed configuration can be used. If cleared or not present, the warning will be displayed. Default is not present.
  * **skipWarningAboutSimultaneousConnections** (Boolean): If set, Tunnelblick will not warn the user when a user tries to connect and there is at least one existing connection. If cleared or not present, the warning will be displayed. Default is not present.
  * **skipWarningThatCannotModifyConfigurationFile** (Boolean): If set, Tunnelblick on Tiger or Leoaprd will not warn the user that any changes made to a configuration file will not be able to be saved. If cleared or not present, the warning will be displayed. Default is not present.
  * **skipWarningThatNameChangeDisabledUpdates** (Boolean): If set Tunnelblick will warn that an update will fail if the name of Tunnelblick.app has been changed by the user. If cleared or not present, the warning will be displayed. Default is not present.
  * **skipWarningAboutNonAdminUpdatingTunnelblick** (Boolean): If set, Tunnelblick will not warn a non-administrator user that an update will require an administrator username/password before the changed updated application can be used. If cleared or not present, the warning will be displayed. Default is not present.

  * **useShadowConfigurationFiles** (Boolean): If set, Tunnelblick will create and use "shadow copies" of configuration files on the local hard drive in a subfolder of `/Library/Application Support/Tunnelblick`. If cleared or not present, the original of each configuration file will be used. Configuration files must be owned by root and have permissions of "644" for security; if the configuration file is on a volume which does not allow this ownership and permissions, shadow copies must be used so the copies can be given the proper ownership and permissions. This happens automatically when the home folder is located on a network volume; it is not necessary to use this preference only when the home folder is on a non-network volume which doesn't allow the required ownership and permissions. The default is not present.
  * **showConnectedDurations** (Boolean): If set, the time that a configuration has been connected is displayed on the configuration's tab in the "Details…" window. If cleared, the time is not displayed. The default is set.

## Per-Configuration Preferences ##
The following preferences must each be prefixed by the name of the configuration file without the ".conf" or ".ovpn" extension. For example, if a configuration file is named "xyz.conf", the preference would be named "xyzautoConnect", "xyz-keychainHasUsernameAndPassword", etc.
  * **autoConnect** (Boolean): If set, Tunnelblick will connect using the configuration when it Tunnelblick is launched. If cleared or not present, the user must connect manually. The user may specify this using the "Automatically Connect on Launch" check box on the "Details…" window tab for the configuration. The default is not present (check box not checked).
  * **useDNS** (Boolean): If set, Tunnelblick will use scripts before and after a connection is made to save and restore the computer's DNS and WINS settings. If cleared or not present, no save and restore will be done. The user may specify this using the "Set Namserver" check box on the "Details…" window tab for the configuration. The default is set (check box checked).
  * **-notMonitoringConnection** (Boolean): If set, Tunnelblick will monitor the network and restart the connection if changes to the network DNS or WINS configurations are detected. If cleared or not present, no monitoring will be done. The user may specify this using the "Monitor Connection" check box on the "Details…" window tab for the configuration. This preference is ignored, and the check box is disabled, if the "useDNS" preference is not set (i.e., the "Set Nameserver" check box is not set). The default is set (check box checked).
  * **disableEditConfiguration** (Boolean): If set, the "Edit Configuration" button on the "Details…" window tab for the configuration will be dimmed and disabled. If cleared or not present, the button will be enabled. The default is not present.
  * **-useDownRootPlugin** (Boolean): If set, Tunnelblick will use its built-in "openvpn-down-root.so" plugin to allow the configuration file to use the "user" and "group" options to stop running the OpenVPN process as root once a connection has been established (as a security measure). See [Using Tunnelblick](UsingTunnelblick.md) for details. The default is not present.
  * **-keychainHasPrivateKey** (Boolean): If set, the user's Keychain contains the connection's private key, and Tunnelblick will use it when needed without interacting with the user. If cleared or not present, the user will be asked for the private key if the connection requires it. This preference is set when the user checks the "Save to Keychain" check box on the dialog which asks for the private key. If this preference is forced, it has a special meaning: the check box is not displayed, the private key is not stored in the user's Keychain, and the user is asked each time the connection requires it. The default is not present.
  * **-keychainHasUsernameAndPassword** (Boolean): If set, the user's Keychain contains the connection's username and password, and Tunnelblick will use them when needed without interacting with the user. If cleared or not present, the user will be asked for the username and password if the connection requires it. This preference is set when the user checks the "Save to Keychain" check box on the dialog which asks for the username and password. If this preference is forced, it has a special meaning: the check box is not displayed, the username and password are not stored in the user's Keychain, and the user is asked each time the connection requires them. The default is not present.

## Preferences That Tunnelblick Uses Internally ##
  * **haveDealtWithSparkle1dot5b6** (Boolean): If set, Tunnelblick has reset the Sparkle Updater preferences for Sparkle version 1.5b6, so the user will be or has been asked about automatically checking for updates and including system profile information. If cleared, this has not been done yet. See the "updateCheckAutomatically" and "updateSendProfileInfo" preferences. The default is not present; Tunnelblick maintains this preference automatically. This preference is ignored if the "updateCheckAutomatically" and "updateSendProfileInfo" preferences are both forced (to any value).
  * **detailsWindowFrame**: The size and position of the "OpenVPN Log” window when it was last closed.
  * **detailsWindowFrameVersion**: The version of Tunnelblick that saved the detailsWindowFrame preference.

## Sparkle Updater Preferences ##
All preferences starting with the letters "SU" are preferences used privately by Sparkle Updater (the program used for Tunnelblick's update mechanism). They cannot be forced and should not be modified. They include:
  * **SUEnableAutomaticChecks** (Boolean)
  * **SUSendProfileInfo** (Boolean)
  * **SUAutomaticallyUpdate** (Boolean)
  * **SULastCheckTime** (Date/time)
  * **SULastProfileSubmissionDate** (Date/time)
  * **SUHasLaunchedBefore** (Boolean)

## Preferences in Tunnelblick 3.1beta01 ##
Tunnelblick version 3.1beta01 (build 1494) includes "Tunnelblick VPN Configurations" (.tblk packages), which can specify default values for preferences. See [Packages Proposal](PackagesProposal.md) for details.

The following additional preferences are available beginning in Tunnelblick version 3.1beta01 (build 1494):

**disableShareConfigurationButton** is a boolean which may be used to inhibit the display of the "Share configuration" / "Make configuration private" button. If absent or false, the button is displayed for all configurations, but is enabled only for Tunnelblick VPN Connection (.tblk) configurations that are not Deployed; it is disabled (dimmed) for  non-.tblk and Deployed configurations.

**usePrivateConfigurationsWithDeployedOnes** and **useSharedConfigurationsWithDeployedOnes** are booleans which may be used in a Deployed version of Tunnelblick (see [Deploying Tunnelblick](cDeployingTunnelblick.md)) to allow simultaneous display of configurations from the Private (~/Library/Application Support/Tunnelblick/Configurations) and Shared (/Library/Application Support/Tunnelblick/Shared) folders, respectively. These preferences must be forced -- they will be ignored if they are not forced.

**skipWarningAboutIgnoredConfigurations** is a boolean which controls display of the warning that one or more configurations are being ignored. Configurations are ignored if there are higher priority configurations with the same name. Priorities are, from highest to lowest:
  1. Deployed .tlbk configurations
  1. Deployed .ovpn and .conf configurations
  1. Shared .tblk configurations
  1. Private .tblk configurations
  1. Private .ovpn and .conf configurations


## Document History ##
  * 2010-02-05
    * Created.
  * 2010-02-15
    * Edits for 3.0
  * 2010-04-26
    * Added section about preferences in Tunnelblick version 3.1beta


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###