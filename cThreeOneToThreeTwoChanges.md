

&lt;hr&gt;



For a list of all changes, see the [Release Notes](RlsNotes.md).



&lt;hr&gt;



## Major Changes from Version 3.1 to Version 3.2 ##

  * Tunnelblick 3.2 is compatible with OS X 10.4 through 10.7 (Tiger, Leopard, Snow Leopard, and Lion).

  * Includes OpenVPN 2.2.1, OpenSSL library 1.0.0e, PKCS#11 1.09.

  * Adds [AppleScript support](wAppleScriptSupport.md).

  * The VPN login window now allows copy/cut/paste of usernames and paste of passwords and passphrases.

  * A new VPN Details… window includes much more information and gives the user more control over preferences and settings.

  * Tunnelblick includes complete Catalan, Czech, German, Spanish, French, Hungarian, Korean, Norwegian, Dutch, Polish, Portuguese, Russian, Swedish, and Chinese (simplified) localization.

  * The following scripts may be included in a Tunnelblick VPN Configuration (.tblk package):
    * The 'pre-connect.sh' script is executed (as root) before Tunnelblick would unload and/or load the tun or tap kexts (whether or not any unload or load takes place).
    * The 'post-tun-tap-load.sh' script is executed (as root) after Tunnelblick unloads and/or loads the tun or tap kexts (whether or not any unload or load takes place). Thus, the script is executed immediately before starting OpenVPN.
    * The 'connected.sh' script is executed (as root) when a configuration connects. This script is executed only if Tunnelblick is running at the time of the event, which may not be the case for 'when computer starts' configurations.
    * The 'reconnecting.sh' script is executed (as root) when OpenVPN loses the VPN connection and is trying to reconnect. This script is executed only if Tunnelblick is running at the time of the event, which may not be the case for 'when computer starts' configurations.
    * The 'post-disconnect.sh' script is executed (as root) after OpenVPN has closed the connection. This script is executed only if Tunnelblick is running at the time of the event, which may not be the case for 'when computer starts' configurations.

  * Tunnelblick VPN Configurations ('.tblk' packages) may now be uninstalled. If the 'TBUninstall' key is included in a Tunnelblick VPN Configuration's Info.plist (with any value), the installed configuration that has corresponding attributes (install location, bundle ID) will be uninstalled. If the key is the string 'ignoreError' (without the quote marks), any failures in the uninstall process will not be reported to the user.

  * Higher 'verb' levels may be used without performance degradation.

  * If Tunnelblick.app/Contents/Resources/Deploy is empty, backups of the Deploy folder are deleted. (This lets a user easily install a fresh un-Deployed Tunnelblick over a Deployed version.)

  * A new leasewatch script is used when 'Monitor connection' is checked. It is more tolerant of unimportant changes. The old script and behavior may be used by specifying 'Set nameserver (3.1)'.

  * New per-configration preference 'XXX-leasewatchOptions' (where XXX is the name of the configuration) consists of '-i' followed by the letters d, a, s, n, g, w to ignore the DomainName, ServerAddresses, SearchDomains, NetBIOSName, Workgroup, and WINSAddresses, respectively. If not present, all items are monitored. Example: to ignore WINS changes completely, use '-ingw'.

  * Includes both OpenVPN 2.1.4 and OpenVPN 2.2.1. The latest version (2.2.1) will be used unless a different version is selected from the 'Preferences' pane of the 'VPN Details…' window.

  * Sleep/wake change: When the computer wakes up, it now tries to reconnect all configurations that were connected, or were in the process of being connected, when it went to sleep. (Previously, Tunnelblick only tried to reconnect only those configurations that were connected when the computer went to sleep.)

  * Unloading of the foo.tap and foo.tun kexts is now attempted only if they are already loaded (previously, it was always attempted and errors were ignored).

  * Application can now be updated even if its name is not Tunnelblick.app.

  * Sorts configurations numerically (e.g., config2, config4, config35 instead of config2, config35, config4).

  * Shows a splash screen during program startup and installation.

  * Several changes to preferences and forced-preferences:
    * If the 'doNotShowAddConfigurationMenuItem' preference is set, the 'Add a Configuration' menu item will not be shown even if there are no configurations.
    * Added the following preferences; each does what its name implies:
      * doNotShowVpnDetailsMenuItem
      * disableAdvancedButton
      * disableCheckNowButton
      * disableResetDisabledWarningsButton
      * disableCopyLogToClipboardButton
      * disableAddConfigurationButton    (disables the '+' button)
      * disableRemoveConfigurationButton (disables the '-' button)
      * disableWorkOnConfigurationButton (disables the 'gear' button)
      * disableRenameConfigurationMenuItem
      * disableDuplicateConfigurationMenuItem
      * disableMakeConfigurationPrivateOrSharedMenuItem
      * disableExamineOpenVpnConfigurationFileMenuItem
      * disableShowOpenVpnLogInFinderMenuItem
      * disableDeleteConfigurationCredentialsInKeychainMenuItem
    * Removed the 'disableShareConfigurationButton' preference.
    * Removed the 'doNotShowForcedPreferenceMenuItems' preference.
    * Removed the 'doNotShowKeyboardShortcutSubmenu' preference.
    * Removed the 'doNotShowOptionsSubmenu' preference.

  * Fixes problems with fast user switching (previously, user switches were ignored, which caused problems if Tunnelblick was used by more than one user and could cause the Tunnelblick icon to indicate no VPN connection when one existed):
    * When a user is switched out, all configurations that are not set to 'connect when computer starts' will be disconnected unless the per-connection '-doNotDisconnectOnFastUserSwitch' preference is set true.
    * When a user is switched in, Tunnelblick will attempt to connect any configurations that were connected at the time the user was switched out but are no longer connected unless the per-connection '-doNotReconnectOnFastUserSwitch' preference is set true.

  * Fixes many bugs.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS