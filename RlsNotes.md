<font size='3'>Release Notes for Tunnelblick</font>




---


## Version 3.5 ##

**3.5beta06 build 4211 (2015-01-22)**

  * Uses a launchd daemon instead of an SUID helper to start OpenVPN on OS X Version 10.5 ("Leopard") and higher.
  * Updates Arabic, Japanese, and Chinese (traditional) localization.
  * Fixes problems with IP address checking on OS X 10.10 ("Yosemite").
  * Fixes problems with the VPN login or passphrase window appearing when waking from sleep or the displays change.
  * Fixes a problem that caused an older version of the tun/tap kexts to be used on OS X 10.6-10.8.
  * Fixes problems with certain malformed updates to Tunnelblick or to configurations.
  * Fixes a problem if certain errors occurred during an update.
  * Fixes a problem showing the failure notification window when an install fails.
  * Fixes a minor memory leak.


---


**3.5beta04 build 4198 (2015-01-08)**

  * <font color='red'>SECURITY UPDATE:</font>**Includes OpenSSL 1.0.1k. See [OpenSSL Security Advisory 08 Jan 2015](https://www.openssl.org/news/secadv_20150108.txt).
  * Adds easy-rsa version 3.0-rc2 to the easy-rsa folder.
  * Adds the per-configuration '-waitForDHCPInfoIfTap' preference which, for TAP configurations, causes the 'up' script to wait until the DHCP info has been processed before continuing with the VPN setup.
  * Adds the 'managementPortStartingPortNumber' preference, which specifies the port number Tunnelblick uses for communication with OpenVPN. If the port is unavailable, successive ports will be tried until an available port is found.
  * Includes complete localization in 20 languages.
  * Flushes DNS cache even if no DNS changes are made by Tunnelblick.
  * Logs additional information about DNS servers being used when connected to the VPN.
  * Fixes problems when Tunnelblick is denied access to the Keychain.
  * Fixes the tab sequencing in the VPN username/password dialog.**



---


**3.5beta02 build 4165 (2014-12-02)**

  * <font color='red'>SECURITY UPDATE:</font>**Includes OpenVPN 2.3.6.  See [OpenVPN Security Announcement-97597e732b](https://community.openvpn.net/openvpn/wiki/SecurityAnnouncement-97597e732b).
  * Includes complete localization in 18 languages including Danish and Greek and partial localization in 7 others, including Arabic and Bulgarian.
  * Uses new (2014-11-04) tun/tap kexts when on OS X 10.9 or 10.10 ("Mavericks" or "Yosemite").
  * Includes new status icon animation which clarifies the connected/connecting/disconnected VPN status -- thanks to William Faulk.
  * Adds the ability to save only the VPN username to the Keychain without saving the VPN password.
  * Adds ability to localize configuration names (and folder names).
  * Moves the 'VPN Details…' menu item to be above the configurations. May be disabled with the 'putVpnDetailsAtBottom' preference is set TRUE.
  * Recreates the status icon only when necessary.
  * Centers the login or passphrase window in the new screen when a screen change occurs or if the computer awakens from sleep unless the 'doNotRedisplayLoginOrPassphraseWindowAtScreenChangeOrWakeFromSleep' preference is set to TRUE.
  * Deletes log files not modified in the last week.
  * An empty name for an 'added menu item' (or the name after translation) causes the item to be skipped.
  * Adds crash report log entries for Tunnelblick components such as openvpn and atsystemstart to the 'Diagnostic Info'.
  * Flushes DNS cache via 'discoveryutil udnsflushcaches' and 'discoveryutil mdnsflushcache' if available.
  * Fixes a problem that caused double-clicks on configurations to not be processed when a window was left open.
  * Fixes several problems with Tunnelblick's handling of 'private keys' (passphrases).
  * Fixes a problem with updates to Deployed versions of Tunnelblick and a problem causing failures on OS X 10.4 ('Tiger').
  * Fixes a problem renaming configurations.
  * Fixes visibility problems with the standard status icon in 'dark mode' on OS X 10.10 ('Yosemite').
  * Fixes problems on OS X 10.4 and 10.5 Intel machines using OpenVPN versions higher than 2.2.1.
  * Fixes a problem with invalid permissions in IconSets contents.
  * Fixes problems that caused digital signature checking to fail on OS X 10.5.
  * Fixes a problem with password and passphrase windows.
  * Fixes status window icon animation.
  * Fixes typo of Feetu Nyrhinen's name on the Info panel.
  * Fixes a problem that caused the 'tun' kext to not be loaded even if 'dev-node tun' was specified in the OpenVPN configuration file.**



---


## Version 3.4 ##

**3.4.3 build 4055.4198 (2015-01-08)**

  * <font color='red'>SECURITY UPDATE:</font>**Includes OpenSSL 1.0.1K. See [OpenSSL Security Advisory 08 Jan 2015](https://www.openssl.org/news/secadv_20150108.txt).**



---


**3.4.2 build 4055.4161 (2014-12-01)**

  * <font color='red'>SECURITY UPDATE:</font>**Includes OpenVPN 2.3.6. See [OpenVPN Security Announcement-97597e732b](https://community.openvpn.net/openvpn/wiki/SecurityAnnouncement-97597e732b).**



---


**3.4.1 build 4054 (2014-10-15)**

  * <font color='red'>SECURITY UPDATE:</font>**Includes OpenSSL 1.0.1j. See [OpenSSL Security Advisory (15 Oct 2014)](https://www.openssl.org/news/secadv_20141015.txt).**



---


**3.4.0 build 4007 (2014-10-03)**

  * <font color='red'>SECURITY UPDATE:</font>**Identical to 3.4beta38 (except for version and build numbers).**



---


**3.4beta38 build 4002 (2014-10-01)**

  * <font color='red'>SECURITY UPDATE:</font>**Fixes several security vulnerabilities.**

  * Includes only OpenVPN 2.3.4. (OpenVPN 2.2.1 is no longer included.)

  * Adds a 'Set DNS after routes have been set up' checkbox to the 'Advanced' settings window.

  * Secures all configurations (shared, private, and shadow) when Tunnelblick is installed.

  * Removes a message that the 'Place icon next to Spotlight icon' checkbox is not available on OS X 10.9 ('Mavericks') and higher.

  * Includes better logging when a forced preference overrides a user-specified preference.

  * Includes preparation for localizing configuration names and Deployed menu commands and Welcome windows.

  * Fixes a problem installing configurations that have both .ovpn and .conf files.

  * Fixes a problem that causes graphic artifacts to appear in the list of configurations in the VPN Details window.

  * Fixes several problems involving rebranded and "Deployed" versions of Tunnelblick.



---


**3.4beta36 build 3945 (2014-09-02)**

  * Fixes a problem on OS X 10.9.5 ('Mavericks') and 10.10 ('Yosemite') that causes spurious warnings that 'This version has been tampered with'.

  * Re-enables the 'Place icon next to Spotlight icon' checkbox on OS X 10.9 ('Mavericks') and higher.



---


**3.4beta34 build 3935 (2014-08-07)**

  * <font color='red'>SECURITY UPDATE:</font>**Updates Tunnelblick's embedded OpenSSL to version 1.0.1i from version 1.0.1h. See [https://www.openssl.org/news/secadv\_20140806.txt](https://www.openssl.org/news/secadv_20140806.txt) and [https://community.openvpn.net/openvpn/wiki/VulnerabilitiesFixedInOpenSSL1.0.1i](https://community.openvpn.net/openvpn/wiki/VulnerabilitiesFixedInOpenSSL1.0.1i) for details.**

  * Includes better handling of computer sleep/wake and fast user switching.

  * Removes OpenVPN version 2.2.3, leaving 2.2.1 and 2.3.4.

  * Holding down the 'Option' key while triple-clicking the Tunnelblick icon opens the 'VPN Details...' window centered on the display.

  * Includes a new key, 'TBKeepExistingFilesList', for updatable configurations.

  * Fixes a problem which caused the Info.plist in certain Tunnelblick VPN Configurations to be ignored while installing the Configuration.

  * Fixes a problem that caused Tunnelblick to not recognize a semicolon (';') character as the start of a comment in an OpenVPN configuration file.

  * Fixes a problem that mistakenly allowed Tunnelblick to run and generate errors if it was in /Applications but its name was not Tunnelblick.app.

  * Fixes several problems with updatable configurations.



---


**3.4beta32 build 3904 (2014-07-17)**

  * Adds the ability to have Tunnelblick VPN Configurations updated the same way that Tunnelblick is updated. See [Updatable Configurations](cUpdatableConfigurations.md) for details.

  * Uses launchd instead of login items to control the launch of Tunnelblick when the user logs in.

  * Fixes a problem installing configurations with 'TBPreference...' or 'TBAlwaysSetPreference' Info.plist entries.

  * Fixes a problem installing configurations that that are inside Contents/Resources folders.

  * Fixes a problem installing configurations when logged in as a 'standard' user (i.e., a non-administrator).

  * Fixes a problem on OS X 10.9 and higher which caused Tunnelblick to try to access login items that were on network volumes.

  * Fixes a problem which caused Tunnelblick to launch at login if the user had last quit Tunnelblick via Command-Q instead of using the 'Quit Tunnelblick' menu command.

  * Fixes a minor memory leak.



---


**3.4beta30 build 3893 (2014-07-08)**

  * Includes major enhancements to installing configurations:
    * Installs OpenVPN configuration files ('.ovpn' or '.conf' files) when they are double-clicked.
    * Installs OpenVPN configuration files automatically if they are in a 'auto-install' or '.auto-install' folder when Tunnelblick is installed.
    * Multiple OpenVPN configuration files may be included in a Tunnelblick VPN Configuration ('.tblk'); when the .tblk is installed, each of the OpenVPN configurations will be installed as a separate configuration.
    * Does more extensive checking of OpenVPN configuration files:
      * They must have correct paths (relative or absolute) to key, certificate, and other files.
      * They must not contain 'Windows only' options.
      * They must not contain options reserved for use by Tunnelblick.
    * Adds an 'Apply to all' checkbox when installing configurations.
    * Allows non-printable characters (such as Unicode characters) anywhere in an OpenVPN configuration file.

  * Adds a condensed copy of the configuration file (without comments or empty lines) to the diagnostic info.

  * Includes preparation for updatable .tblk configurations.

  * Includes LZO version 2.08.

  * Changes many warning dialogs so they do not block other Tunnelblick operations.

  * Includes a new 'Inhibit automatic update checking and IP Address checking' checkbox on the 'Preferences' page. Checking it disables all Internet activity by the Tunnelblick program itself (but not by OpenVPN), overriding any other settings that allow such activity. The checkbox is unchecked by default.

  * Disables the 'Reset the primary interface after disconnecting' checkbox if 'Set DNS/WINS' is not set to 'Set nameserver'.

  * Includes changes to avoid compiler warnings on Xcode 5 and 6.

  * Fixes a problem with OpenVPN mis-identifying an x86\_64 build as an i386 build. (Thanks to Harold Molina-Bulla.)

  * Fixes a problem with names of OpenVPN folders.

  * Fixes a misleading message in the installer log.

  * Fixes several problems with Unicode characters.



---


**3.4beta28 build 3872 (2014-06-12)**

  * Includes OpenSSL library version 1.0.1h, which fixes several security vulnerabilities (see [OpenSSL Security Advisory 05 Jun 2014](http://www.openssl.org/news/secadv_20140605.txt)).

  * Includes (some) preparation for OS X 10.10 ('Yosemite').

  * Fixes a problem that crashes Tunnelblick if the 'VPN Details…' window is displayed when there no configurations.

  * Fixes a problem that caused a failure to update the connection status and statistics.

  * Fixes problems flushing the DNS cache on OS X 10.5 and 10.10 ('Leopard' and 'Yosemite').

  * Fixes problems resetting the primary interface.

  * Fixes problems installing or deleting configurations that contain locked files or folders.

  * Fixes problems that caused the notification window to fail to appear when the pointer hovers over the Tunnelblick icon on OS X 10.5 ('Leopard').

  * Fixes a problem that caused delays and invalid Console log messages on OS X 10.9 and 10.10 ('Mavericks' and 'Yosemite').

  * Fixes a problem when a .tblk contains an up.sh or down.sh script.

  * Fixes several minor cosmetic problems, including the mislabeling of the 'Copy Diagnostic Info to Clipboard' button on OS X 10.4 and 10.5 ('Tiger' and 'Leopard').


---


**3.4beta26 build 3828 (2014-05-02)**

  * Replaces OpenVPN version 2.3.3 with version 2.3.4. Tunnelblick now contains OpenVPN versions 2.2.1, 2.3.2, and 2.3.4.

  * Quits Tunnelblick faster.

  * Warns about OpenVPN options that are not allowed on OS X because they are allowed only on Windows.

  * Excludes the value of the 'installationUID' preference from the diagnostic info.

  * Includes better OpenVPN version detection.

  * Includes better handling of invalid preferences.

  * Includes additional error logging.

  * Fixes problems with NUL characters in configuration files.

  * Fixes a problem that caused some 'Connect' button presses to be ignored.

  * Fixes a problem that caused some settings to be ignored.

  * Fixes a problem that caused spurious Console log entries about unknown preferences.

  * Fixes a problem with the position of the help button on Preferences panel.

  * Fixes a problem deleting old logs.

  * Fixes a problem with permissions on non-.tblk folders in Deploy.

  * Fixes a non-reachable double-free.

  * Fixes a minor memory leak.


---


**3.4beta24 build 3806 (2014-04-18)**

  * Includes OpenVPN 2.3.3 (as well as 2.2.1 and 2.3.2).

  * Adds additional security checking of programs that Tunnelblick runs as root.

  * Moves the 'Copy Diagnostic Info to Clipboard' to the main part of the 'VPN Details…' window.

  * Adds a 'quit' command for AppleScript which terminates Tunnelblick properly so it is not launched at the next login.

  * When 'sanitizing' a configuration file for 'Examine OpenVPN Configuration File' and 'Copy Diagnostic Info to Clipboard', Tunnelblick strips lines that appear between lines that contain '-----BEGIN' and '-----END' (even in comments). (This strips certificates and keys created by Open Access.)

  * On OS X 10.6.8 and higher when using OpenVPN 2.3.3 and higher in a TUN configuration, Tunnelblick no longer automatically loads the tunnelblick tun kernel extension (kext). In this situation, OpenVPN will use the UTUN device driver built into OS X.

  * Warns user if the system clock is not set correctly.

  * Checks Tunnelblick preference files for errors.

  * Changes words for 'In:' and 'Out:' in Russian.

  * Adds additional information to a warning message about LSSharedFileListItemResolve returning an error.

  * Fixes a problem that caused the initial notification window to remain visible even when the pointer moved away from the Tunnelblick icon.

  * Fixes a problem that could cause loss of embedded certificates and/or keys when editing a configuration file.

  * Fixes problems that sometimes caused the 'Load tun' and 'Load tap' settings to be ignored.

  * Fixes a problem which sometimes displayed an incomplete window title for the 'VPN Details…' window in languages other than English.

  * Fixes a problem which sometimes caused a crash.

  * Fixes a small memory leak.


---


**3.4beta22 build 3789 (2014-04-08)**

  * Includes OpenSSL library version 1.0.1g, which does not have the ["heartbeat" vulnerability](https://www.openssl.org/news/secadv_20140407.txt).

  * Shows a notification window for the most recently connected configuration upon mouseover of the Tunnelblick icon even if no configuration has been connected since Tunnelblick was launched.

  * On OS X 10.9 ('Mavericks'), forces the Tunnelblick icon to be in the standard status icon position (to the left of other icons at the time Tunnelblick is launched). This is a temporary limitation until a bug in OS X is fixed.

  * Allows non-ASCII characters (such as accented characters) in token names, passphrases, usernames, and passwords. (Available only in OpenVPN 2.3 and higher.)

  * Includes version 1.11 of pkcs11-helper.

  * Can use kill() to send SIGTERM to OpenVPN processes.

  * Reorders options to OpenVPN that are required by Tunnelblick so they cannot be overridden by entries in the configuration file.

  * Sets the 'IV\_GUI\_VER' environment variable when starting OpenVPN.

  * Adds a list of any unusual files in a .tblk to the diagnostic info.

  * Includes additional information in the Tunnelblick log if a script fails.

  * Displays 'OpenVPN is a registered trademark of OpenVPN Technologies, Inc.' on the Info panel.

  * Adds an entry to the Console Log if there are options in the configuration file that will be ignored because they are used by Tunnelblick or are incompatible with Tunnelblick.

  * Fixes problems prepending new search domains and a new domain name to search domains. MANY THANKS TO ANDREW DAUGHERITY FOR FINDING AND FIXING THIS BUG.

  * Fixes a problem that caused some scripts to fail.

  * Fixes a problem selecting the default OpenVPN version for one or more configurations.

  * Fixes a cosmetic error in the output of 'Copy Diagnostic Info to Clipboard'.

  * Fixes a problem with 'Connect when computer starts' configurations that have a name that contains '-S'.


---


**3.4beta20 build 3727 (2014-01-16)**

  * Replaces embedded OpenSSL 1.0.1e with 1.0.1f (see [OpenSSL Vulnerabilities](http://www.openssl.org/news/vulnerabilities.html)).

  * Checks and corrects ownership/permissions of launchd .plist files when Tunnelblick launches.

  * Adds a list of loaded non-Apple kexts to the 'Diagnostic Info'.

  * Adds detailed logging if the 'DB-ALL' preference is set.

  * Inhibits use of the default 'openvpn' domain if the per-configuration '-doNotUseDefaultDomain' preference is set.

  * Fixes a problem that caused the Tunnelblick icon to show the connection status incorrectly.

  * Fixes two problems that caused settings to change without the user requesting the change.

  * Fixes a problem with the Tunnelblick icon disappearing for five seconds after the computer wakes from sleep if Tunnelblick is not set to check for an apparent public IP address change.

  * Fixes a problem using Tunnelblick after the 'Examine OpenVPN Configuration' command is used.

  * Fixes a problem that caused the incorrect display of the 'Do not show on Tunnelblick menu' checkbox.

  * Fixes a problem with repeated unexpected disconnection sounds when waking from sleep and there is no Internet access and 'Check if the apparent public IP address changed after connecting' is not enabled.

  * Fixes a problem recognizing OpenVPN processes that were running when Tunnelblick was launched.

  * Fixes a problem starting more than one configuration 'when computer starts'.

  * Fixes a problem disconnecting with the disconnect menu command or notification window disconnect button.

  * Fixes a problem disconnecting configurations set to start when the computer starts.

  * Fixes problems when Tunnelblick is launched when more than one configuration is already connecting or connected.

  * Fixes a problem that caused the 'VPN Details…' window to move to the center of the screen when the 'VPN Details…' menu command is clicked.

  * Fixes a problem reconnecting after computer sleep if 'Check if apparent public IP address changes after connecting' is not checked.

  * Fixes several minor memory leaks.


---


**3.4beta18 build 3704 (2013-12-18)**

  * Includes a new status icon (the icon in the menu bar) more in keeping with recent OS X aesthetics and which includes Retina images. (The old icon may be selected as the 'Tunnelblick 3.3 icon' on the Appearance panel of the 'VPN Details…' window.)

  * Changes to Tunnelblick's handling of computer sleep:
    * Adds a 'Disconnect when computer goes to sleep' checkbox on the 'Advanced' settings window; it is checked by default.
    * Before reconnecting any configurations after the computer wakes up from sleep, Tunnelblick waits for an Internet connection if checking that the IP address changed is allowed; or waits for a timeout period (the default is five seconds) if it is not.

  * Allows selection of the display on which notification windows will be shown if multiple displays are available.

  * Adds a 'Run MTU maximum size test after connecting' checkbox to the 'While Connected' tab of the 'Advanced' window.

  * Adds a button to obtain additional information when the user is asked if Tunnelblick should check for apparent public IP address changes. Clicking the button displays the new "Privacy and Security" wiki page.

  * Adds a symlink named 'default' to the Contents/Resources/openvpn' folder. The link points to the default OpenVPN binary, which is the lowest version of OpenVPN included in that copy of Tunnelblick. (Useful for scripts: they needn't search the 'openvpn' folder to find an OpenVPN binary.)

  * Fixes a problem converting some OpenVPN configurations to Tunnelblick VPN Configurations.


---


**3.4beta16 build 3679 (2013-11-22)**

  * Adds the 'Include anonymous profile information' checkbox to the Preferences panel.

  * Adds the 'Keep connected' checkbox to the Settings tab of Configurations panel. This will attempt to reconnect a configuration if OpenVPN crashes.

  * Allows the 'Place next to Spotlight icon' checkbox (on the Appearance panel) to be checked on OS X 10.9 ("Mavericks") with multiple displays if 'Displays have separate spaces' is unchecked in the Mission Control preferences. (Otherwise the checkbox may not be checked on Mavericks with multiple displays.)

  * Allows a 'preferences.plist' file in auto-install or .auto-install folders. Tunnelblick references specified in the file are set as specified when Tunnelblick is installed. (See https://code.google.com/p/tunnelblick/wiki/cPkgs#Automatic_Installation for details.)

  * Checks for apparent IP address changes asynchronously.

  * Sets timer tolerances on Mavericks for lower power use.

  * Adds Tunnelblick settings and specific configuration settings to the info generated by 'Copy Diagnostic Info to Clipboard'.

  * Complains about OpenVPN options that cause writing to a file that is not specified with an absolute path.

  * Does not allow files larger than 10MB to be in Tunnelblick VPN Configurations.

  * Complains about files whose paths contain prohibited characters.

  * Increases the number of status windows allowed on the screen from 64 to 4096.

  * Fixes a problem with connection restarts (caused, for example, by the OpenVPN --ping-restart option) by not starting OpenVPN with the -up-restart option. The -up-restart option can be added to the configuration file if it is needed. Note: The OpenVPN configuration must not contain the 'persist-tun' option or restarts will still fail. (The OpenVPN documentation seems to be incorrect with respect to these two options.)

  * Fixes a problem that sometimes caused a crash when a configuration is deleted or Tunnelblick is started with no configurations.

  * Fixes a problem that sometimes caused a crash when an OpenVPN configuration file contains UTF-8 characters.

  * Fixes a problem that sometimes caused a crash during the installation of a Tunnelblick VPN Configuration if a file is empty.

  * Fixes a problem that sometimes caused a hang during a disconnection which encountered certain errors.

  * Fixes problems that sometimes caused Tunnelblick to refuse to install Tunnelblick VPN Configurations containing certain OpenVPN configuration file constructs or that contain files in subfolders.

  * Fixes a problem that caused Tunnelblick to sometimes ignore OpenVPN configurations.

  * Fixes a problem that caused unpredictable behavior if a free port could not be found for managing OpenVPN.

  * Fixes a problem that caused an unnecessary warning in the system log about an unknown preference.


---


**3.4beta14 build 3649 (2013-10-25)**

  * Implements 'Examine OpenVPN Configuration File' for Shared and Deployed configurations.

  * On OS X 10.6 ('Snow Leopard') and higher, allows the user to select multiple configurations in the VPN Details… window and then change settings for all of the selected configurations. (A confirmation dialog prevents inadvertent changes.) The only setting that cannot be changed this way is the 'Connect' setting.

  * Adds per-configuration 'OpenVPN version' selection to the VPN Details… window and removes 'OpenVPN version' selection from the Preferences panel.

  * Adds a per-configuration 'Check that the apparent IP address changed after connecting' checkbox to the Advanced settings window.

  * Replaces the 'Use Tunnelblick tun/tap drivers' checkbox on the Advanced settings window with pop-up buttons (one for tun and one for tap) that allow the user to always use the driver, never use the driver, or have Tunnelblick decide whether to use the driver based on the configuration file.

  * Adds a button on the Utilities panel that opens a web page with instructions for uninstalling Tunnelblick.

  * Moves 'Show configuration on Tunnelblick menu' to the Advanced settings window.

  * Fixes a problem when installing a Tunnelblick VPN Configuration that includes CR-LF sequences in the OpenVPN configuration file.

  * Fixes a problem with the appearance of the bottom of the configuration list in the VPN Details… window.

  * Fixes a memory leak that would occur only under very unusual conditions.


---


**3.4beta12 build 3636 (2013-10-17)**

  * Logs more information if a sound is not found.

  * Fixes a problem on OS X 10.5 and 10.6 ('Leopard' and 'Snow Leopard') that caused incorrect 'invalid signature' warnings.

  * Fixes a problem on OS X 10.9 ('Mavericks') that caused Tunnelblick to crash when launched on some systems.

  * Fixes a problem on OS X 10.8 and 10.9 ('Mountain Lion' and 'Mavericks') with 'Copy Diagnostic Info to Clipboard'.

  * Fixes a problem that causes the log to 'freeze' under certain circumstances.

  * Fixes a problem when user-supplied scripts output a lot of text to stdout or stderr.

  * Fixes an error in the Italian (IT) localization.


---


**3.4beta10 build 3614 (2013-10-05)**

  * Includes additional security checking when Tunnelblick is launched:
    * Verifies the digital signature of the Sparkle framework.
    * Verifies that kexts and digital signatures are secured.
    * Verifies that everything in the application is writable only by root.
    * Checks that the system folders used by Tunnelblick are secure.

  * Includes better error checking and reporting when installing a Tunnelblick VPN Configuration.

  * Option-click (Alt-click) on most configuration settings checkboxes allows the choice of changing the setting for the selected configuration or for all configurations.

  * Includes a new per-configuration preference, '-openvpnVersion' which can contain an OpenVPN version string (for example, '2.3.2'). A value of '-' will use the latest version of OpenVPN. If set, it will override the application-wide 'openvpnVersion' preference. (This preference cannot yet be set by the GUI.)

  * Includes the ability to use an asterisk ("`*`") in front of the name of a connection-specific preference to indicate that all configurations should use that preference by default. (A specific preference for a configuration will override this default.)

  * Includes a new TBAlwaysSetPreference key to Info.plist of a .tblk. It is used like TBPreference, but it causes the preference to be set 'always' -- it is reset each time the configuration is connected and when Tunnelblick starts up.

  * Recovers more gracefully from OpenVPN crashes.

  * Includes better help on the 'Advanced' settings page.

  * Fixes a problem that caused settings on the 'While Connected' tab of the 'Advanced' window to be ignored.

  * Fixes a problem with the release of a DHCP lease on a TAP connection when using the 'Set name server' DNS/WINS setting.

  * Fixes a problem that did not allow .crl files in a Tunnelblick VPN Configuration (.tblk).

  * Fixes several problems that caused failures when installing a Tunnelblick VPN Configuration.


---


**3.4beta08 build 3576 (2013-09-06)**

  * Fixes a problem that caused update checks to fail.


---


**3.4beta06 build 3571 (2013-09-06)**

  * Fixes a crash when accessing checkboxes on the 'Advanced' window.

  * Uses digitally signed tun and tap kexts on OS X 10.9 ('Mavericks').

  * Recovers more gracefully from some crashes.

  * Fixes a typo in the ES (Spanish) translation.

  * Fixes a problem that sometimes caused a spurious entry in the Console Log.

  * Fixes a small memory leak.


---


**3.4beta04 build 3555 (2013-08-21)**

  * Uses https: for update checks and loading all update information. (Updates are still protected by being digitally signed; this is an additional level of security.)

  * Uses https: for IP address checks that use a domain name in the URL to test DNS. Tunnelblick continues to use http: for IP address checks that use an IP address in the URL, which is done if the first IP address check (using a domain name in the URL) fails. This is done because https: requires a domain name, not an IP address. There is no information sent out that is encrypted, and the received data for this request is discarded, so encryption is not necessary, anyway.

  * Adds a 'Check for updates to beta versions' checkbox in the 'Updates' section of the 'Preferences' panel, which controls the new 'updateCheckBetas' preference. If checked, Tunnelblick will check for new beta versions of Tunnelblick that are available for update, otherwise, Tunnelblick will check for new stable versions. Checked by default when running a beta version, unchecked by default when running a stable version.

> Note: This feature may be used to revert to the latest stable version from a later beta version: if this is un-checked in a beta version, Tunnelblick will offer to install the latest stable version, which may be a 'downgrade' from the beta version to an earlier stable version.

  * Uses new URLs when checking for updates:
    * 'https://www.tunnelblick.net/appcast-s.rss' to check for new stable versions,
> > > and
    * 'https://www.tunnelblick.net/appcast-b.rss' to check for new beta versions.


> The URL of customized or Deployed versions of Tunnelblick that contain a non-standard update feed URL have '-s' or '-b' appended to the last component of the URL before the extension (e.g. 'http://aaa/bbb/ccc.ddd' becomes 'http://aaa/bbb/ccc-s.ddd' or 'http://aaa/bbb/ccc-b.ddd' to check for stable and beta versions, respectively).

  * Updates several Dutch (NL) translations; a Italian (IT) translation, and a Chinese (simplified) translation.

  * Fixes spacing problems on the 'Preferences' tab that occur when there is only one version of OpenPVN included in Tunnelblick.


---


**3.4beta02 build 3550 (2013-08-07)**

> This is the first beta release of Tunnelblick 3.4 and includes fixes for several bugs in 3.3.0:

  * Removed some extra debug logging.

  * Includes a stack trace in the error message sent to the Console Log when a fatal error occurs on OS X 10.6 and higher.

  * Fixes a problem installing Tunnelblick VPN Configurations that include .cer, .cert, .der, .p12, .p7b, .p7c, or .pfx files.

  * Fixes problems that cause Tunnelblick to crash or hang if there were no configurations and the 'VPN Details…' menu command was clicked.

  * Fixes problems when there are no configurations.

  * Fixes problems that can lead to a Tunnelblick crash or hang under an unusual OS X error condition.

  * Fixes problems that cause Tunnelblick to crash or hang if many changes to the configurations are made very quickly.

  * Fixes a problem that caused the 'Welcome to Tunnelblick' window to appear more than once when multiple changes to the configurations are made very quickly.

  * Fixes a problem that caused the status window to fail to appear when the pointer is over the Tunnelblick icon after checking or un-checking the 'Place `[`the Tunnelblick icon`]` next to Spotlight icon' checkbox in the 'Appearances' panel.

  * Fixes a problem on OS X 10.9 ('Mavericks') that caused Tunnelblick to always launch after login even if it had quit before logging out.

  * Fixes a problem on OS X 10.9 ('Mavericks') that sometimes caused the Tunnelblick icon to disappear from the status bar on a computer with multiple displays.

  * Fixes a problem displaying the hex code for invalid characters in files.

  * Fixes a typo in message sent to the Console Log about 'login intems' (changed to 'login items').


---


## Older Versions ##

Release notes for older versions are available on the [Old Release Notes page](RlsNotesOld.md).


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###