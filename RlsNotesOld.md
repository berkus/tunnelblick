<font size='3'>Old Release Notes for Tunnelblick</font>




---


## Newer Versions ##

Release notes for newer versions are available on the [Release Notes page](RlsNotes.md).



---


## Version 3.3 ##

**3.3.4 build 3518.3872 (2014-06-12)**

  * Includes OpenSSL library version 1.0.1h, which fixes several security vulnerabilities (see [OpenSSL Security Advisory 05 Jun 2014](http://www.openssl.org/news/secadv_20140605.txt)).

**3.3.2 build 3518.3792 (2014-04-08)**

  * Includes OpenSSL library version 1.0.1g, which does not have the ["heartbeat" vulnerability](https://www.openssl.org/news/secadv_20140407.txt).

  * Implements 'Examine OpenVPN Configuration File' for Shared and Deployed configurations.

  * Includes a better Console log message when a sound is not found.

  * Option-click on a checkbox allows the option of changing a setting for all configurations.

  * Allows .crl files in a .tblk.

  * Allows non-printing characters in comments and single- and double-quotes and after a backslash in OpenVPN configuration files and scripts that are being coverted into Tunnelblick VPN Configurations.

  * Checks that additional system folders are secure.

  * Adds TBAlwaysSetPreference key to Info.plist of a .tblk. It is like TBPreference, but it causes the preference to be set 'always' -- it is reset each time the configuration is connected and when Tunnelblick starts up.

  * Adds a new per-configuration preference, '-openvpnVersion' which can contain an OpenVPN version string (for example, '2.3.2'). If set, it will override the application-wide 'openvpnVersion' preference.

  * Adds the ability to use an asterisk (`*`) in front of the name of a connection-specific preference to indicate that all configurations should use that preference by default. (A specific preference for a configuration will override this default.)

  * Some error messages were made clearer and more specific.

  * Does better error checking and reports problems directly to the user when installing a Tunnelblick VPN Configuration.

  * Clarifies help on the 'Advanced' settings page.

  * Attempts to recover when OpenVPN crashes without having run the 'down' script by running the 'route-pre-down' and 'down' scripts from Tunnelblick and runs the 'route- pre-down' script to release the DHCP lease on a TAP connection if needed.

  * Verifies the digital signature of Sparkle framework.

  * Verifies that kexts and digital signatures are secured.

  * Verifies that everything in the application is only writable by root.

  * Attempts to display an error message in a GUI window if it can't display normal windows.

  * Adds clearer error handling for problems with Applications, Library, and Application Support folders that are insecure.

  * Signs kexts for Mavericks.

  * Includes additional logging of ownership changes made by installer.

  * Catches SIGTRAP if not debugging and add signal name to Console output.

  * Fixes crash when accessing checkboxes on 'Advanced' window.

  * Includes a Sparkle patch to allow downgrades to stable versions from beta versions.

  * Uses https: for update checks and loading all update information and adds the ability check for updates to beta versions and to 'downgrade' from beta to stable. (Updates are still protected by being digitally signed so they cannot be forged; this is an additional level of security.)

  * Uses https: for IP address checks that use a domain name in the URL to test DNS. (Tunnelblick continues to use http: for IP address checks that use an IP address in the URL, which is done if the first IP address check (using a domain name in the URL) fails.)

  * Adds a new checkbox in the 'Updates' section of the 'Preferences' panel: 'Check for updates to beta versions', which controls the 'updateCheckBetas' preference. If checked, Tunnelblick will check for new beta versions of Tunnelblick that are available for update, otherwise, Tunnelblick will check for new stable versions. Checked by default when running a beta version, unchecked by default when running a stable version. Note: If this is un-checked in a beta version, Tunnelblick will offer to install the latest stable version, which may be a 'downgrade' from the beta version to an earlier stable version.

  * Uses new URLs when checking for updates:
    * 'https://www.tunnelblick.net/appcast-s.rss' to check for new stable versions,
> > > and
    * 'https://www.tunnelblick.net/appcast-b.rss' to check for new beta versions.


> The URL of customized or Deployed versions of Tunnelblick that contain a non- standard update feed URL have '-s' or '-b' appended to the last component of the URL before the extension (e.g. 'http://aaa/bbb/ccc.ddd' becomes 'http://aaa/bbb/ccc-s.ddd' or 'http://aaa/bbb/ccc-b.ddd' to check for stable and beta versions, respectively).

  * Removed unused files English.lproj/Description.rtf and English.lproj/Credits.rtf.

  * Adds stack trace to Console Log on fatal error; removes debugging entries from Console Log.

  * Filters CR characters from .sh, .conf, .ovpn, .crt, .key, and .pem files when installing a .tblk.

  * Corrects the name of Chinese (traditional) (ZH\_TW) localizer from 'Pompin Wu' to 'Pomin Wu'.

  * Fixes several problems that caused failures when installing Tunnelblick VPN Configurations.

  * Fixes a problem when installing a Tunnelblick VPN Configuration that includes CR-LF sequences in the OpenVPN configuration file.

  * Fixes a problem on OS X 10.5 and 10.6 ('Leopard' and 'Snow Leopard') that caused spurious 'invalid signature' errors.

  * Fixes a problem that causes the log to 'freeze' under certain conditions.

  * Fixes a problem when Tunnelblick scripts output a lot to stdout or stderr.

  * Fixes a problem with 'Copy Diagnostic Info to Clipboard' on Mountain Lion and Mavericks.

  * Fixes typos in(ZH\_CN), Spanish (ES), Finnish (FI), Italian (IT), Norwegian (NB), Dutch (NL), and Chinese (simplified) translations.

  * Fixes a bug that caused settings on the 'While Connected' tab of the 'Advanced' window to be ignored.

  * Fixes a problem on Mavericks that caused Tunnelblick to crash on launch on some systems.

  * Fixes a problem that caused the status window to fail to appear when the pointer is over the Tunnelblick icon after checking or un-checking the 'Place [Tunnelblick icon](the.md) next to Spotlight icon' checkbox in the 'Appearances' panel.

  * Fixes a problem on OS X 10.9 ('Mavericks') that caused Tunnelblick to always launch after login even if it had quit before logging out.

  * Fixes a problem on OS X 10.9 ('Mavericks') that sometimes caused the Tunnelblick icon to disappear from the status bar on a computer with multiple displays.

  * Fixes a problem that caused the status window to fail to appear when the pointer is over the Tunnelblick icon after checking or un-checking the 'Place [Tunnelblick icon](the.md) next to Spotlight icon' checkbox in the 'Appearances' panel.

  * Fixes a problem on OS X 10.9 ('Mavericks') that caused Tunnelblick to always launch after login even if it had quit before logging out.

  * Fixes a problem on OS X 10.9 ('Mavericks') that sometimes caused the Tunnelblick icon to disappear from the status bar on a computer with multiple displays.

  * Fixes problems that cause Tunnelblick to crash or hang if many changes to the configurations are made very quickly.

  * Fixes a problem that caused the 'Welcome to Tunnelblick' window to appear more than once when multiple changes to the configurations are made very quickly.

  * Fixes problems when there are no configurations.

  * Fixes spacing problems on the 'Preferences' tab that occur when there is only one version of OpenPVN included in Tunnelblick.

  * Fixes problems that can lead to a Tunnelblick crash or hang under an unusual OS X error condition.

  * Fixes problems that cause Tunnelblick to crash or hang if many changes to the configurations are made very quickly.

  * Fixes a problem that caused the 'Welcome to Tunnelblick' window to appear more than once when multiple changes to the configurations are made very quickly.

  * Fixes a problem converting or installing configurations with .cer, .cert, .der, .p12, .p7b, .p7c, and .pfx files; (3) Fixes a problem displaying the hex code for invalid characters in files.

  * Fixes a problem that sometimes caused a spurious entry in the Console Log.

  * Fixes a small memory leak.


---


**3.3 build 3518 (2013-07-22)**

> This is the first stable release of Tunnelblick 3.3. It is identical to version 3.3beta56 except for version information.

> [Summary of Changes from Version 3.2 to Version 3.3](DocumentationForTunnelblick_3_3.md)<br>
<blockquote><a href='cThreeTwoToThreeThreeChanges.md'>Details of Changes from Version 3.2 to Version 3.3</a><br></blockquote>

<hr />

<b>3.3beta56 build 3515 (2013-07-19)</b>

<blockquote>Expected to be the last beta before the 3.3 stable release.</blockquote>

<ul><li>Complete Catalan, Czech, Finnish, French, Hungarian, Italian, Japanese, Korean, Norwegian, Dutch, Portuguese, Russian, Slovak, Swedish, and Chinese (simplified) localization.</li></ul>

<ul><li>Allows the replacement of a Tunnelblick VPN Configuration that has an Info.plist even if it does not have a CFBundleIdentifier entry.</li></ul>

<ul><li>Detects rich text files and files with illegal characters when installing a Tunnelblick VPN Configuration or converting an OpenVPN configuration.</li></ul>

<ul><li>Allows the Info.plist of a Tunnelblick VPN Configuration to be located either in the .tblk folder directly, or in its "Contents" subfolder.</li></ul>

<ul><li>Fixes a problem that sometimes caused an incorrect display of the settings of a Tunnelblick VPN Configuration that had been replaced.</li></ul>

<ul><li>Fixes a problem that caused an unnecessary dialog window to appear when canceling the installation of a Tunnelblick VPN Configuration.</li></ul>

<ul><li>Fixes a problem that sometimes caused no configuration to be selected the first time a freshly-installed Tunnelblick is launched.</li></ul>

<ul><li>Fixes a problem that sometimes caused an invalid OpenVPN version to select the default version of OpenVPN, instead of the latest version.</li></ul>

<ul><li>Fixes a problem that caused overwritten or truncated text in the status window, the 'Advanced' window, and the Log tab of the 'VPN Details…' window in some languages.</li></ul>

<ul><li>Fixes a problem in status window that displays the 'In:' and 'Out:' text incorrectly in languages other than English.</li></ul>

<ul><li>Fixes a problem that caused the 'Remove Credentials' submenu to be too narrow to fit localized text, and updates the Japanese localization with better translations.</li></ul>

<hr />

<b>3.3beta54 build 3415 (2013-06-08)</b>

<ul><li>Includes complete German, Spanish, and Polish localization.</li></ul>

<ul><li>Includes OpenVPN  version 2.3.2.</li></ul>

<ul><li>Adds the ability to edit a configuration name by clicking on it and editing it directly (OS X 10.6 and higher only).</li></ul>

<ul><li>Adds the ability to always use the latest OpenVPN version that is available.</li></ul>

<ul><li>Adds a confirmation dialog if user has no Tunnelblick VPN Configurations and does not want to convert OpenVPN configurations to Tunnelblick VPN Configurations.</li></ul>

<ul><li>Fixes a problem that caused openvpn and down-root.so binaries to not be digitally signed.</li></ul>

<ul><li>Fixes a problem disconnecting configurations using the down-root plugin if killall is allowed.</li></ul>

<ul><li>Fixes a problem with up & down scripts failing when /etc/resolv.conf is empty except for comments.</li></ul>

<ul><li>Fixes a problem that displayed the wrong version of VPN that would be used if the requested version is not available.</li></ul>

<ul><li>Fixes a problem using WiFi after disconnecting if 'Reset the primary interface after disconnecting' is checked.</li></ul>

<ul><li>Fixes a problem converting an OpenVPN configuration that contains an inline key/cert/etc.</li></ul>

<ul><li>Fixes a problem that failed to keep a configuration selected after it was renamed.</li></ul>

<ul><li>Fixes a problem verifying digital signatures of Deployed versions of Tunnelblick.</li></ul>

<ul><li>Fixes a problem that could cause double-freeing of memory.</li></ul>

<ul><li>Fixes a problem that could cause the the status window to show incorrect statistics.</li></ul>

<ul><li>Fixes a problem that could cause credits on Info panel to appear in an incorrect font.</li></ul>


<hr />

<b>3.3beta52 build 3352 (2013-05-20)</b>

<ul><li>Fixes problems converting an OpenVPN configuration file that:<br>
<ul><li>Uses files with extensions that Tunnelblick does not know how to secure properly; or<br>
</li><li>Does not end with a linefeed; or<br>
</li><li>Has '<a href='inline.md'>inline</a> options; or<br>
</li><li>Has a path component that starts with a dot (".").</li></ul></li></ul>

<ul><li>Fixes a problem that caused Tunnelblick to be unable to install a Tunnelblick VPN Configuration (".tblk") that has a path component that starts with a dot (".").</li></ul>

<ul><li>Fixes a problem on OS X 10.4 ("Tiger") that caused the copyright date in the startup screen to be displayed incorrectly.</li></ul>

<ul><li>Fixes a extraneous warning about Info.plist options that do not exist being ignored when installing or converting to a .tblk.</li></ul>

<ul><li>Fixes a minor memory leak.</li></ul>

<hr />

<b>3.3beta50 build 3302 (2013-05-11)</b>

<ul><li>Saves and restores the configuration selected in the configuration list in the 'VPN Details…' window.</li></ul>

<ul><li>Saves and restores folder expansion states in the configuration list in the 'VPN Details…' window.</li></ul>

<ul><li>Fixes a problem converting OpenVPN configuration files that have backslashes in paths.</li></ul>

<ul><li>Fixes a problem converting OpenVPN configuration files that have multiple OpenVPN options using the same file or files with the same name.</li></ul>

<ul><li>Fixes a problem converting OpenVPN configuration files that have script file names that do not have a '.sh' extension.</li></ul>

<ul><li>Fixes a problem displaying line numbers in OpenVPN configuration files in the log when converting OpenVPN configurations.</li></ul>

<ul><li>Fixes a problem that caused Deployed versions to ignore forced preferences.</li></ul>

<hr />

<b>3.3beta48 build 3292 (2013-05-08)</b>

<ul><li>Allows install and launch of a 'Deployed' version of Tunnelblick:<br>
<ul><li>If it is a 'rebranded' version of Tunnelblick (source code modified to use a different name); and<br>
</li><li>If Info.plist does not have 'tunnelblick.net' in the 'updateFeedURL' forced preference (or in SUFeedURL if there is no 'updateFeedURL' forced preference); and<br>
</li><li>If Info.plist does not have 'net.tunnelblick' in the CFBundleIdentifier; and<br>
</li><li>All copies of the program include the Deploy folder. (Even updates must include the Deploy folder. Udpates did not previously require the Deploy folder because it would be restored from backups maintained by the program. The program no longer maintains backups.)</li></ul></li></ul>

<ul><li>Allows the 'skipWarningAboutNoSignature' preference to be forced. This preference inhibits warnings about the application not being digitally signed.</li></ul>

<ul><li>Adds additional DNS information to the Tunnelblick log.</li></ul>

<ul><li>Adds a 'Copy Console Log to Clipboard' button to the Utilities panel.</li></ul>

<ul><li>When installing Tunnelblick VPN Configurations (.tblks) that include nested .tblks inside them, TBReplaceIdentical, TBSharePackage, and TBUninstall in the outer Info.plist will override corresponding entries in the nested .tblks.</li></ul>

<ul><li>No longer  restores the 'Setup:' DNS key in scutil if it isn't needed (some OS X 10.7 setups, and all OS X below 10.7).</li></ul>

<ul><li>Fixes a security issue when installing Tunnelblick VPN Configurations (.tblks).</li></ul>

<ul><li>Fixes a problem in the build of OpenVPN 2.3.1 that caused it to reject the 'keysize' option.</li></ul>

<ul><li>Fixes a problem that caused failures when using auto-install and .auto-install folders to install Tunnelblick VPN Configurations when Tunnelblick is installed.</li></ul>

<ul><li>Fixes a problem that caused 'pre-connect', 'connected.sh', 'reconnecting.sh', and 'post-disconnect.sh' scripts in shared configurations to not be executed.</li></ul>

<ul><li>Fixes a problem when the installer fails when trying to connect an unsecured configuration. (This would only happen if something is drastically wrong with the system, such as incorrect ownership or permissions on /Library).</li></ul>

<hr />

<b>3.3beta46 build 3281 (2013-04-22)</b>

<ul><li><font color='red'>Security</font>: Digitally signs Tunnelblick's copies of OpenVPN.</li></ul>

<ul><li>Includes a 64-bit Intel version of OpenVPN 2.3.1.</li></ul>

<hr />

<b>3.3beta44 build 3276 (2013-04-16)</b>

<ul><li>Fixes a problem when converting an OpenVPN configuration with the 'auth-user-pass' option to a Tunnelblick VPN Configuration.</li></ul>

<ul><li>Fixes a problem updating the configurations display when a configuration is added or deleted.</li></ul>

<hr />

<b>3.3beta42 build 3270 (2013-04-13)</b>

<ul><li>Fixes a problem that caused DHCP over tap connections to fail.</li></ul>

<ul><li>Fixes a problem that caused the failure to install a 'Tunnelblick VPN Configuration'.</li></ul>

<ul><li>Fixes a problem that caused fatal errors in the down script if a '-useDownRootPlugin'preference was set for the configuration but 'user nobody' and 'group nobody' were not used.</li></ul>

<ul><li>Fixes a problem that caused warnings about obsolete preferences.</li></ul>

<ul><li>Fixes a problem that caused the Console log to not be included on the Clipboard when the 'Copy Diagnostic Info to the Clipboard' button is used by a user who is not an administrator.</li></ul>

<ul><li>Diagnostic information now includes the user's status as a 'standard' or 'admin' user.</li></ul>

<hr />

<b>3.3beta40 build 3265 (2013-04-11)</b>

<ul><li>Fixes a problem with Tunnelblick's new 64-bit OpenVPN 2.2.1 by only including the 32-bit versions of OpenVPN.</li></ul>

<hr />

<b>3.3beta38 build 3258 (2013-04-09)</b>

<ul><li>On OS X 10.6 ('Snow Leopard') and higher, Tunnelblick now displays configurations in a way that is similar to the 'List View' in a Finder window: contents of folders can be hidden or exposed by clicking on a disclosure triangle next to the folder name. This may be disabled (and the old way of displaying configurations used) by setting the 'doNotShowOutlineViewOfConfigurations' preference to 'TRUE'.</li></ul>

<ul><li>Replaces OpenVPN version 2.3alpha1 with version 2.3.1, and runs OpenVPN, OpenSSL, and LZO in 64-bit mode when it is available (Intel only) -- many thanks to HAROLD MOLINA-BULLA.</li></ul>

<ul><li>Enhances installation of Tunnelblick VPN Configurations with improved error detection and correction.<br>
<ul><li>The user can now replace an existing configuration with a new one.<br>
</li><li>Tunnelblick now complains about files referenced in the OpenVPN configuration file that do not exist or are accessed via a path instead of just a filename.<br>
</li><li>Tunnelblick now removes CR characters from script files.</li></ul></li></ul>

<ul><li>Changes the 'Copy Log to Clipboard' button to the 'Copy Diagnostic Info to Clipboard' button. The info copied to the clipboard includes the configuration file contents, the log contents, and recent Console log output from Tunnelblick and OpenVPN. (Configuration file contents have inline data removed so as to not disclose private keys.)</li></ul>

<ul><li>Keeps a history of Tunnelblick versions that were launched, and displays the most recently used prior version in the log.</li></ul>

<ul><li>Adds a checkbox to 'Route all traffic through the VPN' on the Advanced settings window. This adds the 'redirect-gateway def1' option to the arguments to OpenVPN. Note that even if is NOT checked, the configuration file may include the option, or the server may push the option.) Default is not checked.</li></ul>

<ul><li>Adds a checkbox to 'Reset the primary interface after disconnecting' on the Advanced settings window. The reset is done via an 'ifconfig down' followed by an 'ifconfig up' on the primary interface after the configuration is disconnected. Default is not checked.</li></ul>

<ul><li>Adds the 'doNotLaunchOnLogin' preference, which causes Tunnelblick to not launch when the user next logs in, even if Tunnelblick was running when the user logged out. This preference cannot be set in the GUI; to set it type the following into Terminal 'defaults write net.tunnelblick.tunnelblick doNotLaunchOnLogin -bool yes'. To restore normal behavior, type 'defaults write net.tunnelblick.tunnelblick doNotLaunchOnLogin -bool yes'.</li></ul>

<ul><li>Allows Tunnelblick.app to have any name (but it still must be installed into /Applications).</li></ul>

<ul><li>Updates LZO to version 2.06.</li></ul>

<ul><li>Updates the help displays.</li></ul>

<ul><li>Changes to the maximum log size now take effect immediately.</li></ul>

<ul><li>Clarified entry made in Console log when Tunnelblick is shut down because of a Command-Q typed by the user.</li></ul>

<ul><li>Fixes a problem that didn't repair invalid ownership of /Library/Application Support/Tunnelblick/Users if the ownership was modified by the user.</li></ul>

<ul><li>Fixes a problem that sometimes caused the last part of the log to be hidden.</li></ul>

<ul><li>Fixes a problem that caused failures when converting a shared Tunnelblick VPN Configurations to be private.</li></ul>

<ul><li>Fixes a problem that allowed the user to resize the VPN Details… window when a panel other than 'Configurations' is being displayed on OS X 10.7 ('Lion') and higher.</li></ul>


<hr />

<b>3.3beta36 build 3228 (2013-03-28)</b>

<ul><li>Removes uninstaller from disk image.</li></ul>

<hr />

<b>3.3beta34 build 3218 (2013-03-27)</b>

<ul><li><font color='red'>Security update:</font> Replaces OpenSSL 1.0.1c with 1.0.1e. (See <a href='http://www.openssl.org/news/secadv_20130204.txt'>http://www.openssl.org/news/secadv_20130204.txt</a> and <a href='http://www.openssl.org/source/exp/CHANGES'>http://www.openssl.org/source/exp/CHANGES</a>).</li></ul>

<ul><li>Accepts multiple "dhcp-option DOMAIN-SEARCH <code>&lt;</code>domain<code>&gt;</code>" options in the configuration file or "pushed" by the VPN server. If present and search domains were not manually set, they are prepended to any search domains that came from DHCP.</li></ul>

<ul><li>Adds an Uninstaller to the Tunnelblick disk image. Double-click to uninstall /Applications/Tunnelblick, or drop a Tunnelblick application onto a copy of the Uninstaller on your boot drive.</li></ul>

<ul><li>Removes the 'Suggestion or Bug Report' menu item. (Only 4 suggestions or bug reports were made among several hundred submissions.)</li></ul>

<ul><li>Displays dialog when a fatal error occurs.</li></ul>

<ul><li>Clearer error messages when a menu icon set is not found.</li></ul>

<ul><li>No longer checks for unsigned updates.</li></ul>

<ul><li>Adds the contents of /etc/resolv.conf to the Tunnelblick log before and after making network configuration changes.</li></ul>

<ul><li>Adds Erwann Thoraval in the credits for French translations on the Info panel for all languages.</li></ul>

<ul><li>Fixes problems indenting configuration subfolders properly in the VPN Details… window.</li></ul>

<ul><li>Fixes misspelling of 'Disconnect' in status window.</li></ul>

<ul><li>Fixes bug that caused the Info panel to display an incorrect OpenVPN version if no OpenVPN version was chosen on the Preferences panel.</li></ul>

<ul><li>Fixes bug that caused the Tunnelblick icon to not respond to clicks properly after a sleep/wake cycle.</li></ul>

<ul><li>Fixes bug that caused the Tunnelblick icon to disappear when an aborted logout takes place.</li></ul>

<ul><li>Fixes bug that caused reverting a configuration to its last secure shadow copy to fail.</li></ul>

<ul><li>Fixes bug that caused a spurious warning if Tunnelblick was Quit by Activity Monitor or reinstallation.</li></ul>

<ul><li>Fixes warnings about unknown preferences.</li></ul>

<ul><li>Complains with an error dialog window if an internal error occurs while trying to check the security of a configuration.</li></ul>

<hr />

<b>3.3beta32 build 3183 (2013-01-05)</b>

<ul><li>Fixes several security issues.</li></ul>

<ul><li>Fixes a problem that disabled all choices in the 'Connect' menu on the 'Settings' tab of the 'Configurations' panel of the 'VPN Details…' window.</li></ul>

<ul><li>Fixes a delay when disconnecting if only one configuration is connected.</li></ul>

<ul><li>Fixes a problem that did not connect a configuration automatically after updating a shadow configuration.</li></ul>

<ul><li>Fixes problems that caused some scripts in Tunnelblick VPN Configurations to not be executed.</li></ul>

<hr />

<b>3.3beta30 build 3176 (2012-12-25)</b>

<ul><li>Updates the easy-rsa programs to fix bugs in the Tunnelblick patches.</li></ul>

<ul><li>Secures the easy-rsa folder and its contents.</li></ul>

<ul><li>Warns the user when trying to install a Tunnelblick VPN Configuration (.tblk) into a Deployed version of Tunnelblick that does not allow shared and/or private configurations.</li></ul>

<ul><li>Fixes bugs in Sparkle Updater's isDeployed and hasDeployBackups detection</li></ul>

<ul><li>Fixes a bug that caused a log message to show permissions as decimal instead of octal.</li></ul>

<ul><li>Fixes a bug that caused installer to fail if /Library/Application Support/Deploy subfolder was not secure."</li></ul>

<ul><li>Fixes bug that caused failures in conversion of an OpenVPN configuration file to a Tunnelblick VPN Configuration (.tblk) if the configuration file does not use separate key, certificate, script, etc. files.</li></ul>

<hr />

<b>3.3beta28 build 3153 (2012-10-24)</b>

<ul><li>Configurations can share credentials (usernames/passwords and pass phrases) so that the credentials need not be entered separately for each configuration. (This may be set on the 'Advanced' settings window's 'VPN Credentials' tab.)</li></ul>

<ul><li>Triple-clicking the Tunnelblick icon opens the VPN Details… window, as does relaunching Tunnelblick from a Dock icon or double-clicking the application in a Finder window.</li></ul>

<ul><li>Adds 'Speak' to list of connect/disconnect sounds. If selected, connections and unexpected disconnections will be announced with the system default voice.</li></ul>

<ul><li>Defaults to use the oldest version of OpenVPN available, instead of the newest version.</li></ul>

<ul><li>Adds the 'Check apparent IP address after connecting' checkbox to the 'Preferences' panel. There is no default; the user is asked whether to do this the first time the user launches Tunnelblick.</li></ul>

<ul><li>Adds the 'Reconnect when computer wakes up from sleep (if connected when computer went to sleep)' checkbox to the 'Advanced' settings panel. The default is to reconnect.</li></ul>

<ul><li>Adds the 'Revert Configuration…' menu command to revert a private configuration to it's last secured (shadow) version.</li></ul>

<ul><li>When requesting a computer administrator username/password for installation, Tunnelblick also shows that it will convert OpenVPN configurations to Tunnelblick VPN Configurations if the user has requested the conversion.</li></ul>

<ul><li>Adds a subcommand to openvpnstart to revert a configuration to when it was last secured.</li></ul>

<ul><li>Does not warn about Tunnelblick being unsigned if Debug build.</li></ul>

<ul><li>Fixes a problem that sometimes left horizontal lines on the list of configurations when the list was scrolled up and down.</li></ul>

<ul><li>Fixes a problem if a configuration was Deployed and needed to be secured.</li></ul>

<ul><li>Fixes a problem that caused the help button on the 'While Connected' tab of the 'Advanced' settings window to do nothing.</li></ul>

<ul><li>Fixes several problems running Tunnelblick on OS X 10.4 ('Tiger').</li></ul>

<ul><li>Inhibits flush of DNS cache on OS X 10.7 or 10.8 if Hands Off is running. (This was included in 3.3beta26.)</li></ul>

<ul><li>Fixes a bug that sometimes caused Tunnelblick installations to fail.</li></ul>

<hr />

<b>3.3beta26 build 3143 (2012-10-12)</b>

<ul><li>Installs, and should be used, only if no Deployed versions of Tunnelblick have previously been installed. (This restriction will probably be removed in later releases.)</li></ul>

<ul><li>Installs even if there are OpenVPN configurations (.ovpn and .conf files).</li></ul>

<ul><li>Offers to convert OpenVPN configurations to Tunnelblick VPN Configurations. OpenVPN configurations that are NOT converted are NOT AVAILABLE for connection.</li></ul>

<ul><li>Recognizes files with '.cert' extensions as certificate files.</li></ul>

<ul><li>When installing a Tunnelblick VPN Configuration, automatically removes path prefixes from configuration file entries that accept paths or commands.</li></ul>

<ul><li>Adds a 'Show when disconnected' checkbox to the 'Notification window' section of the Appearance preferences tab of the 'VPN Details…' window. This is checked by default.</li></ul>

<ul><li>Checks Tunnelblick's digital signature, and warns the user if it is missing or invalid.</li></ul>

<ul><li>Fixes a problem that caused configurations in submenus not to be sorted properly.</li></ul>

<ul><li>Changes the status/notification window's single Connect/Disconnect button to two separate buttons.</li></ul>

<ul><li>Adds more specific error messages when files with unrecognized extensions or folders are in a Tunnelblick VPN Configuration (.tblk) that is being installed.</li></ul>

<ul><li>Removes the 'keyboardShortcutKeyCode' and 'keyboardShortcutModifiers' preferences.</li></ul>

<ul><li>Fixes problems installing from a disk image.</li></ul>

<ul><li>Fixes a problem that disabled the keyboard shortcut (hotkey) until the VPN Details… window was opened.</li></ul>

<ul><li>Fixes a problem causing the Tunnelblick icon to become invisible when changing settings on the 'Appearance' panel.</li></ul>

<ul><li>Fixes a problem displaying a shortened log on OS X 10.4 ('Tiger').</li></ul>

<ul><li>Fixes a problem that caused Tunnelblick to not create a shadow configuration file when installing a Tunnelblick VPN Configuration (.tblk).</li></ul>

<ul><li>Fixes a problem that caused the download statistics shown in the status/notification window to be incorrect.</li></ul>

<hr />

<b>3.3beta24 build 3126 (2012-09-13)</b>

<ul><li>Fixes problems installing from disk image.</li></ul>

<hr />

<b>3.3beta22 build 3117 (2012-09-12)</b>

<ul><li>Installs, and should be used, only if:<br>
<ul><li>All private configurations are Tunnelblick VPN Configurations (.tblk files);<br>
</li><li>It is not a Deployed version; and<br>
</li><li>No Deployed versions of Tunnelblick have previously been installed.</li></ul></li></ul>

<ul><li>Will install to, and may only be run from, /Applications.</li></ul>

<ul><li>Fixes security issues raised by Tunnelblick <a href='https://code.google.com/p/tunnelblick/issues/detail?id=212'>Issue 212</a>.</li></ul>

<hr />

<b>3.3beta21b (2013-01-08)</b>

<ul><li><font color='red'>Security update to prepare for Tunnelblick 3.3beta32.</font><b></li></ul></b>

<ul><li>Fixes problem detecting Deployed versions of Tunnelblick.</li></ul>

<ul><li>Fixes problem detecting that Tunnelblick is not installed in /Applications.</li></ul>

<hr />

<b>3.3beta21a (2012-09-12)</b>

<ul><li>New 'Welcome window' feature:<br>
<ul><li>If a 'Welcome' folder exists as a subfolder of Deploy and contains an 'index.html' file, that file will be displayed as a welcome screen when Tunnelblick is launched.<br>
</li><li>Otherwise, if a 'welcomeURL' preference exists and is being forced, that URL will be displayed as a welcome screen when Tunnelblick is launched.<br>
</li><li>If a 'welcomeWidth' and/or 'welcomeHeight' preference exists, its numeric value will be used for the width or height of the HTML display area of the welcome screen (otherwise, the area will be 500 pixels square).<br>
</li><li>If a 'doNotShowWelcomeDoNotShowAgainCheckbox' preference exists and is true, a 'Do not show this again' checkbox will appear in the welcome window.<br>
</li><li>If a 'skipWelcomeScreen' preference exists and is true, the welcome screen will not be shown.</li></ul></li></ul>

<ul><li>Prevents the display of notification windows for configurations that are disconnected if the 'doNotShowDisconnectedNotificationWindows' preference is true.</li></ul>

<ul><li>Fixes incorrect display of VPN traffic statistics.</li></ul>

<ul><li>Restores support for PowerPC processors and OS X 10.4 ("Tiger")</li></ul>

<ul><li>Prepares for update to 3.3beta22</li></ul>

<hr />

<b>3.3beta20 (2012-08-20)</b>

<ul><li>After installing this version, Tunnelblick can only be updated by a computer administrator.</li></ul>

<ul><li>Attempts IP address check five seconds after a VPN connection is made, with a thirty second timeout. This makes it less likely that the 'No DNS' message will appear when DNS is working properly.</li></ul>

<ul><li>Shows '(Deployed)' in the Info panel for Deployed versions of Tunnelblick.</li></ul>

<ul><li>Refuses to install a signed version of Tunnelblick over a Deployed version unless the signed version has its own Deploy folder.</li></ul>

<ul><li>Adds additional check for valid URL for updates and logs error instead of silently failing to check for updates.</li></ul>

<ul><li>Fixes several problems caused by digital signatures.</li></ul>

<ul><li>Fixes a problem in the standard down script for TAP connections.</li></ul>

<ul><li>Fixes a problem that caused DNS cache flushes to fail silently.</li></ul>

<ul><li>Fixes a problem with route-pre-down scripts if 'user nobody' and 'group nobody' are specified and openvpn-down-root.so is used.</li></ul>

<ul><li>Changes to Sparkle Updater to prepare for later releases</li></ul>

<hr />

<b>3.3beta18 (2012-08-04)</b>

<ul><li>Fixes several problems on Mountain Lion and temporarily adds extra logging to help diagnose problems.</li></ul>

<ul><li>Restores the default 'Set nameserver' DNS/WINS setting to restart when 'SearchDomain' is changed.</li></ul>

<ul><li>Adds a new checkbox on the 'Advanced' settings page that tells Tunnelblick to add the domain name provided by OpenVPN to the start of the list of search domains. This checkbox is disabled and unchecked unless the DNS/WINS setting is set to 'Set nameserver'. Adding the domain name does not take place if the search domains are manually set.</li></ul>

<ul><li>Checks that the computer's apparent public IP address changes when connected to a VPN. This can help diagnose connection and DNS problems. (Tunnelblick asks for permission to do this the first time it is launched for each user on a computer.)</li></ul>

<ul><li>Fixes a crash of the Tunnelblick UI in certain complex circumstances.</li></ul>

<hr />

<b>3.3beta16 (2012-07-27)</b>

<ul><li>Fixes a problem that stops updates from being installed.</li></ul>

<hr />

<b>3.3beta14 (2012-07-27)</b>

<ul><li>Fixes problems with DNS on OS X 10.8 ("Mountain Lion") when using the default DNS/WINS setting of 'Set nameserver'.</li></ul>

<hr />

<b>3.3beta12 (2012-07-24)</b>

<ul><li>Reverts to OpenVPN 2.3-alpha1 to fix problems with the build of OpenVPN 2.3_alpha2.</li></ul>

<ul><li>Fixes problems causing long delays when logging out or sleeping, restarting, or shutting down the computer.</li></ul>

<ul><li>Fixes a problem causing the Tunnelblick icon to disappear.</li></ul>

<hr />

<b>3.3beta10 (2012-07-20)</b>

<ul><li>Fixes a problem disabling network connection monitoring.</li></ul>

<ul><li>Fixes a problem with OpenVPN version 2.3alpha2 being 'unknown' and disabling scripts.</li></ul>

<ul><li>Fixes a problem implementing preferences having to do with what to do when there are changes to the network settings.</li></ul>

<hr />

<b>3.3beta08 (2012-07-19)</b>

<ul><li>SECURITY UPDATE: Updates OpenSSL to 1.0.1c (<a href='http://www.openssl.org/news/secadv_20120510.txt'>OpenSSL's advisory</a>)</li></ul>

<ul><li>Tunnelblick is now digitally signed by an Apple 'identified developer', so that it may be installed with the default settings for Gatekeeper on OS X 10.8 ("Mountain Lion").</li></ul>

<ul><li>Updates to and uses OpenVPN version 2.3alpha2 by default. OpenVPN version 2.2.1 can be used instead by selecting it in the 'Preferences' panel of the 'VPN Details…' window.</li></ul>

<ul><li>Fixes a problem that caused configurations to connect and disconnect repeatedly on OS X 10.8 ("Mountain Lion").</li></ul>

<ul><li>Fixes a problem that caused a warning on the console log that the 'SUSkippedVersion' preference was unknown.</li></ul>

<hr />

<b>3.3beta06 (2012-05-08)</b>

<ul><li>Enhances security by digitally signing Sparkle.framework (signed versions only).</li></ul>

<ul><li>Fixes a problem installing or launching Tunnelblick when a .tblk exists but is not a folder (i.e., not an OS X package).</li></ul>

<ul><li>Fixes problems on OS X 10.4 ('Tiger').</li></ul>

<ul><li>Fixes a problem that sometimes caused updates to unsigned versions of Tunnelblick instead of to signed versions.<br>Note: this was not caused by a problem in Tunnelblick itself -- it was caused by a misconfiguration on the tunnelblick.net website (the website used to check for updates). The misconfiguration was fixed on 2012-05-05 at 23:54 +04:00.</li></ul>

<hr />

<b>3.3beta04 (2012-04-28)</b>

<ul><li>SECURITY UPDATE: Replaces OpenSSL 1.0.1 with 1.0.1b.</li></ul>

<ul><li>Enhances security by making all of the application's contents owned by root.</li></ul>

<ul><li>Fixes bug when on OS X 10.4 ("Tiger") that used an unavailable method.</li></ul>

<ul><li>Fixes invalid links in Sparkle (which implements updates) FR_CA localization.</li></ul>

<ul><li>Fixes <a href='https://code.google.com/p/tunnelblick/issues/detail?id=205'>Issue 205</a> (notification windows overlapping each other).</li></ul>

<ul><li>Fixes some compiler warnings from Xcode 4.</li></ul>

<hr />

<b>3.3beta02 (2012-03-16)</b>

<ul><li>Includes several changes with respect to notification windows:<br>
<ul><li>Notification windows display the total amount of data uploaded and downloaded and recent up and down transfer rates for client connections.<br>
</li><li>When the pointer (mouse) is over the Tunnelblick icon in the menu bar, the notification windows for all configurations that have been active since Tunnelblick was launched are displayed. (This may be changed on the 'Appearances' panel of the 'VPN Details…' window.)<br>
</li><li>Notification windows do not fade away if the pointer is over any notification window (or the Tunnelblick icon, as described above).<br>
</li><li>Notification windows for disconnected configurations have a 'Connect' button.<br>
</li><li>Fixes a bug that caused notification windows to appear in Mission Control on Lion even though they were closed.</li></ul></li></ul>

<ul><li>Adds Openvpn 2.3alpha1, removes OpenVPN 2.1.4.</li></ul>

<ul><li>Adds a 'Utilities' tab to the VPN Details… window. It includes:<br>
<ul><li>A 'Terminate all OpenVPN processes' button.<br>
</li><li>A 'Run easy-rsa in Terminal' button.<br>
</li><li>Click the '?' button on the tab for more information about these features.</li></ul></li></ul>

<ul><li>Adds the ability to have a 'route-pre-down.tunnelblick.sh' script that is run before closing a connection. Tunnelblick's 'Set Nameserver' scripts use this to release a TAP device's DHCP lease. This feature (and the DHCP lease release) is available only when using OpenVPN 2.3alpha1 and only in <a href='cPkgs.md'>Tunnelblick VPN Configurations</a>.</li></ul>

<ul><li>Includes a customized version of OpenVPN's 'easy-rsa' 2.0  command-line scripts for creating certificates and keys.</li></ul>

<ul><li>Adds two AppleScript nouns for configurations: 'bytesIn' and 'bytesOut' report bytes in or out through a client connection since Tunnelblick was launched.</li></ul>

<ul><li>Adds a 'Suggestion or Bug Report…' menu item to beta versions of Tunnelblick unless the 'doNotShowSuggestionOrBugReportMenuItem' preference is true.</li></ul>

<ul><li>Includes OpenSSL 1.0.1.</li></ul>

<ul><li>Does not try to connect if the OpenVPN log file could not be created.</li></ul>

<ul><li>Does not allow Unicode characters in usernames, passwords, and private keys (OpenVPN does not accept them).</li></ul>

<ul><li>Includes more debugging information when OpenVPN starts or fails to start.</li></ul>

<ul><li>Includes enhancements to the Tunnelblick build/clean process (see <a href='https://code.google.com/p/tunnelblick/source/detail?r=1965'>r1965</a> for details).</li></ul>

<ul><li>Includes preparations for Mountain Lion.</li></ul>

<ul><li>Disconnects a configuration if a Tunnelblick VPN Configuration script returns a non-zero (mod 256) result.</li></ul>

<ul><li>Logs explanations of why a disconnection occurred.</li></ul>

<ul><li>Logs Tunnelblick VPN Configuration script execution and result codes.</li></ul>

<ul><li>Logs unknown 'foreign_option's found by the standard up script.</li></ul>

<ul><li>Fixes a bug in log display of the command line used to start OpenVPN (cosmetic problem).</li></ul>

<ul><li>Fixes a bug causing loss of contents in the log display if the log contains invalid characters.</li></ul>

<ul><li>Fixes problems with the log display if the display gets large.</li></ul>

<ul><li>Fixes a problem with 'While connected' actions not always being saved in the 'Advanced' settings window.</li></ul>

<ul><li>Fixes a problem when there are no icon sets.</li></ul>

<ul><li>Fixes several compiler warnings detected by Xcode 4.</li></ul>

<hr />

<h2>Version 3.2</h2>

<b>3.2.9 (2013-05-14)</b>

<ul><li>Preparation for updating to Tunnelblick 3.3.</li></ul>

<ul><li>Only this and later versions will be able to update to Tunnelblick 3.3 when it becomes available as a stable release.</li></ul>

<hr />

<b>3.2.8 (2012-08-10)</b>

<ul><li>Fixes several problems caused by digital signatures.<br>
<hr /></li></ul>

<b>3.2.7 (2012-08-06)</b>

<ul><li>SECURITY UPDATE: Includes OpenSSL 1.0.0j, the latest security update to the 1.0.0 branch of OpenSSL.</li></ul>

<ul><li>Tunnelblick 3.2 has reverted to using the OpenSSL 1.0.0 branch (from the 1.0.1 branch) because of problems with OpenSSL 1.0.1b on some PowerPC computers.</li></ul>

<ul><li>Fixes a problem when a Tunnelblick VPN Configuration (.tblk) is not a folder.</li></ul>

<ul><li>Fixes crashes of the Tunnelblick UI under two separate sets of complex circumstances.</li></ul>

<hr />

<b>3.2.6 (2012-05-03)</b>

<ul><li>Fixes a crash on OS X 10.4 ("Tiger") or PowerPC.</li></ul>

<hr />

<b>3.2.5 (2012-04-29)</b>

<ul><li>Fixes a problem with the digital signatures of updates in 3.2.4.</li></ul>

<hr />

<b>3.2.4 (2012-04-27)</b>

<ul><li>SECURITY UPDATE: Replaces OpenSSL 1.0.0g with 1.0.1b.</li></ul>

<ul><li>Fixes a problem with 'While connected' actions not always being saved in the 'Advanced' settings window.</li></ul>

<ul><li>Disconnects a configuration if a Tunnelblick VPN Configuration script returns a non-zero (mod 256) result.</li></ul>

<ul><li>Logs explanations of why a disconnection occurred.</li></ul>

<ul><li>Logs Tunnelblick VPN Configuration script execution and result codes.</li></ul>

<ul><li>Logs unknown 'foreign_option's found by the standard up script.</li></ul>

<ul><li>Fixes a problem when there are no icon sets.</li></ul>

<ul><li>Fixes bugs in OpenVPN's easy-rsa scripts that cause errors when the path to easy-rsa contains whitespace.</li></ul>

<ul><li>Fixes several compiler warnings detected by Xcode 4.</li></ul>

<hr />

<b>3.2.3 (2012-01-25)</b>

<ul><li>Fixes a security vulnerability in OpenSSL by updating to OpenSSL version 1.0.0g. See <a href='http://www.openssl.org/news/secadv_20120118.txt'>http://www.openssl.org/news/secadv_20120118.txt</a> for details.</li></ul>

<ul><li>Fixes a bug that sometimes caused repeated restarts of a connection when the search domain changed after the connection was established.</li></ul>

<ul><li>"Deployed" versions that update from the Tunnelblick website always update to unsigned versions to avoid problems with the OS X Keychain.</li></ul>

<ul><li>Fixes some French localization.</li></ul>

<ul><li>At launch, if Tunnelblick is updating from the official Tunnelblick site and has an invalid digital signature (for example, the program is a Deployed version or has been modified in some other way by the user), an update to an <i>unsigned</i> version of Tunnelblick will be offered immediately -- even if the user has turned off automatic updates -- unless the "updateCheckAutomatically" preference is being forced to false or the user is not an administrator and the "onlyAdminCanUpdate' preference is false or not present.</li></ul>

<hr />

<b>3.2.2 (2012-01-09)</b>

<ul><li>Fixes six OpenSSL security flaws by updating OpenSSL from 1.0.0e to 1.0.0f. See <a href='http://www.openssl.org/news/secadv_20120104.txt'>http://www.openssl.org/news/secadv_20120104.txt</a> for details.</li></ul>

<ul><li>Fixes a problem that caused a restart of the connection as a result of a DHCP renewal.</li></ul>

<ul><li>Fixes failure to ask what should be done when the user enters an incorrect private key (passphrase).</li></ul>

<hr />

<b>3.2.1 (2011-12-29)</b>

<ul><li>Fixes a problem preventing installation or updates for some users on OS X 10.4.</li></ul>

<ul><li>Fixes problems connecting (loading tun/tap kexts) for some users.</li></ul>

<hr />

<b>3.2 (2011-12-19)</b>

<ul><li>Stable 3.2 release -- not a beta release.</li></ul>

<ul><li>Fixes a security vulnerability found in Tunnelblick 3.2beta36. (See <a href='vulnerability20111219FAQ.md'>2011-12-19 Tunnelblick Vulnerability FAQ</a> for details.)</li></ul>

<ul><li>Includes complete Japanese localization by Yoshihisa Kawamoto.</li></ul>

<ul><li>Fixes a memory leak and a problem that caused a failure to localize tabs in the "Advanced" settings window.</li></ul>

<hr />

<b>3.2beta36 (2011-12-10)</b>

<ul><li>Includes additional Japanese localization by Yoshihisa Kawamoto.</li></ul>

<ul><li>Adds more control over what Tunnelblick does when a network setting changes. Controls are located on the "While Connected" tab of the Advanced configuration settings. (These controls may not be modified if the per-configuration 'CONFIGURATIONNAME-leasewatchOptions' preference is present. That preference is now deprecated.)</li></ul>

<ul><li>Includes fixes to format of Czech localization of credits.</li></ul>

<ul><li>Includes additional log entry if ExecuteAuthorized fails.</li></ul>

<ul><li>When installing and securing Tunnelblick, logs a warning but continues to install if the private configurations folder is not present. (Previously, the installation was abandoned if the private configurations folder was not present.)</li></ul>

<hr />

<b>3.2beta34 (2011-11-27)</b>

<ul><li>Includes a Hungarian translation by Marcell Szabo, and a Czech translation by Petr Šrajer.</li></ul>

<ul><li>Includes the latest Tuntap release (version 20111101) for Snow Leopard and higher (Tunnelblick uses version 19990913 for Tiger and Leopard). This should fix the "kernel: Failed to add membership to all-hosts multicast address on interface" error in Lion.</li></ul>

<ul><li>Fixes a bug in the build process that causes an extra copy of a tun/tap kext to be stored inside each tun/tap kext when a build has already been done.</li></ul>

<ul><li>Fixes problems updating Tunnelblick caused by digital signatures on Deployed versions. When installing updates on a non-customized version of Tunnelblick (i.e., the Info.plist SUFeedURL entry is "<a href='http://tunnelblick.net/appcast.rss'>http://tunnelblick.net/appcast.rss</a>"):<br>
<ul><li>If the "updateSigned" preference is set, the application will be updated with a signed version;<br>
</li><li>Otherwise, if the "updateUnsigned" preference is set, the application will be updated with an unsigned version;<br>
</li><li>Otherwise, versions before 3.2beta34 are updated with signed versions; versions 3.2beta34 and higher are updated with signed versions only if they are themselves signed, otherwise they are updated with unsigned versions.<br>
</li><li>"Signed" does not refer to the update itself, which is always digitally signed for authenticity. It refers to the Tunnelblick.app application being signed so that the updated version can use Keychain items without OS X prompting the user for permission.<br>
</li><li>See <a href='cDigitalSignatures.md'>Tunnelblick and Digital Signatures</a> for more details.</li></ul></li></ul>

<ul><li>For an "Unsigned Release" build, " Unsigned" is appended to CFBundleShortVersionString (the marketing version string). Similarly, for a "Debug" build, " Debug" is appended.</li></ul>

<hr />

<b>3.2beta32 (2011-10-12)</b>

<ul><li>Includes OpenSSL version 1.0.0e.</li></ul>

<ul><li>Complete Polish localization by Magdelena Zajac and Łukasz M.</li></ul>

<ul><li>Improved French localization by Olivier Borowski.</li></ul>

<ul><li>Removes extra logging by Tuntap kexts introduced in 3.2beta30.</li></ul>

<ul><li>Does not allow a configuration to be renamed or made private or made shared unless the configuration is disconnected.</li></ul>

<ul><li>Fixes a problem with configurations set to connect 'when computer starts'.</li></ul>

<ul><li>Fixes a problem not accepting digits in domain names pushed by the VPN server. Now accepts A-Z, a-z, 0-9, '-', and '.' in domain names. Does NOT accept internationalized domain names.</li></ul>

<hr />

<b>3.2beta30 (2011-08-31)</b>

<ul><li>Includes an experimental version of the Tuntap kexts (device drivers) that are used when running on OS X 10.7 "Lion". This should fix problems with kernel panics on some processors. (The older, stable versions of the drivers are used on OS X 10.4 - 10.6.)</li></ul>

<ul><li>Includes both OpenVPN 2.1.4 and OpenVPN 2.2.1. The latest version (2.2.1) will be used unless a different version is selected in the 'Preferences' pane of the 'VPN Details…' window.</li></ul>

<ul><li>Includes complete localization for Catalan, German, Spanish, French, Korean, Norwegian, Dutch, Portuguese, Russian, Swedish, and Chinese (simplified).</li></ul>

<ul><li>Changes ownership/permissions of key, certificate, etc. files in a .tblk from root:wheel 0600 to root:admin 0640. This allows easier access to them for Admins (who could always access them with sudo anyway).</li></ul>

<ul><li>Translates the "Double-click to begin" message that appears in the disk image window to several more languages.</li></ul>

<ul><li>Several changes to preferences and forced-preferences:<br>
<ul><li>If the 'doNotShowAddConfigurationMenuItem' preference is set, the 'Add a Configuration' menu item will not be shown even if there are no configurations.<br>
</li><li>Added the following preferences; each does what its name implies:<br>
<ul><li>doNotShowVpnDetailsMenuItem<br>
</li><li>disableAdvancedButton<br>
</li><li>disableCheckNowButton<br>
</li><li>disableResetDisabledWarningsButton<br>
</li><li>disableCopyLogToClipboardButton<br>
</li><li>disableAddConfigurationButton    (disables the '+' button)<br>
</li><li>disableRemoveConfigurationButton (disables the '-' button)<br>
</li><li>disableWorkOnConfigurationButton (disables the 'gear' button)<br>
</li><li>disableRenameConfigurationMenuItem<br>
</li><li>disableDuplicateConfigurationMenuItem<br>
</li><li>disableMakeConfigurationPrivateOrSharedMenuItem<br>
</li><li>disableExamineOpenVpnConfigurationFileMenuItem<br>
</li><li>disableShowOpenVpnLogInFinderMenuItem<br>
</li><li>disableDeleteConfigurationCredentialsInKeychainMenuItem<br>
</li></ul></li></ul></li><li>Removed the 'disableShareConfigurationButton' preference.<br>
</li><li>Removed the 'doNotShowForcedPreferenceMenuItems' preference.<br>
</li><li>Removed the 'doNotShowKeyboardShortcutSubmenu' preference.<br>
</li><li>Removed the 'doNotShowOptionsSubmenu' preference.</li></ul>

<ul><li>Several bugfixes:<br>
<ul><li>Fixes a bug that caused the splash window to not be closed properly and thus appear in Exposé even after Tunnelblick has finished launching.<br>
</li><li>Fixes a bug that caused abnormally high CPU usage after closing the 'VPN Details…' window if it was displaying the 'Info' panel.<br>
</li><li>Fixes a bug that tried to create a shadow copy of configuration files that were unsecured in Deploy or Shared. Now asks to secure them instead.<br>
</li><li>Fixes a bug that caused problems for 'connect when computer starts' configurations when the configuration is in a subfolder or the configuration's name contains slashes, dashes, or periods.<br>
</li><li>Fixes a bug that caused a forced 'updateFeedURL' preference to be ignored. (Note: this preference can only be forced; an 'updateFeedURL' user preference will be ignored for security  reasons).<br>
</li><li>Fixes a bug that caused the 'updateCheckInterval' preference to be ignored<br>
</li><li>Fixes a bug that caused the 'Notification window' button to be enabled even if the 'connectionWindowDisplayCriteria' preference was forced.<br>
</li><li>Fixes a bug that caused the Tunnelblick icon to continue to blink when AppleScript was used to 'connect all', even after all connections had been successfully made.</li></ul></li></ul>

<hr />

<b>3.2beta28 (2011-07-31)</b>

<ul><li>Johan Nilsson and Tim Malmström have provided Swedish localization.</li></ul>

<ul><li>Prevents kernel panics on OS X 10.7 "Lion" by reverting to OpenVPN 2.1.4.</li></ul>

<ul><li>Tunnelblick can now be updated even if its name is not Tunnelblick.app.</li></ul>

<ul><li>A splash window with status information appears while Tunnelblick is starting up. It will not be displayed if 'Display window while Tunnelblick is starting up' is unchecked on the 'Appearance' panel of the 'VPN Details…' window. (Controlled by the 'doNotShowSplashWindow' preference.)</li></ul>

<ul><li>You can now select and copy the version information in the Info panel.</li></ul>

<ul><li>Fixes bug that caused a failure to display an error message and a many-second delay when user tries to set a non-.tblk to start when the computer starts.</li></ul>

<hr />

<b>3.2beta26 (2011-07-20)</b>

<ul><li>Aleix Dorca has provided a complete Catalan localization.<br>
</li><li>Emma Segev and Tjalling Soldatt have provided complete Dutch localization.<br>
</li><li>Peter K. O'Connor has provided complete Chinese (simplified) localization.<br>
</li><li>Dennis Ukhanov, Eugene Trufanov, Nail Gilmanov, & Victor Ptichkin have provided complete Russian localization.</li></ul>

<ul><li>Changes the 'Show/Hide Configuration on Tunnelblick Menu' menu command to be the 'Show on menu' checkbox on the 'Settings' tab.</li></ul>

<ul><li>Un-rebrands the license description unless the 'doNotUnrebrandLicenseDescription' preference is set.</li></ul>

<ul><li>Fixes bugs when menu icon sets are not available.</li></ul>

<ul><li>Fixes bugs when updating Tunnelblick while a connection is active.</li></ul>

<ul><li>Fixes console warning about unrecognized preference.</li></ul>

<hr />

<b>3.2beta24 (2011-07-14)</b>

<ul><li>Complete German localization by Marcus Schneider.<br>
</li><li>Complete French localization by Jeremy Sherman.<br>
</li><li>Complete Korean localization by Kyoungmin Kim.<br>
</li><li>Complete Norwegian localization by Jon Luberth.<br>
</li><li>Complete Portuguese localization by Denis Volpato Martins.</li></ul>

<ul><li>Includes OpenVPN version 2.2.1.</li></ul>

<ul><li>Now loads sounds each time the Configurations panel is displayed, so any sounds added by the user can be used immediately.</li></ul>

<ul><li>Adds protection against race conditions in sleeping and quitting.</li></ul>

<ul><li>The credits and license description on the Info panel are now localized.</li></ul>

<ul><li>Fixes a bug that didn't update 'Settings' tab items properly when a different configuration was selected in the 'Configurations' panel.<br>
</li><li>Fixes a bug that caused several items to appear in English instead of the preferred language, even if a preferred language translation of the item was available.<br>
</li><li>Fixes a bug that caused the 'Glass' sound to be used when a tunnel is established and the 'Basso' sound to be used when a tunnel was torn down if the preference for the sound was set to 'None'<br>
</li><li>Fixes a bug that caused the 'Advanced' window to pop up in front of any other application's window when the notification window appears.<br>
</li><li>Fixes a bug that ignored the Enter and Escape keys when entering a VPN username/password or passphrase.<br>
</li><li>Fixes a bug that caused the 'Glass' sound to be used when a tunnel is established and the 'Basso' sound to be used when a tunnel was torn down if the preference for the sound was set to 'None'<br>
</li><li>Fixes a bug that caused problems and failed to properly warn the user that a private configuration cannot be set to start when the computer starts.<br>
</li><li>Fixes several small memory leaks.</li></ul>


<hr />

<b>3.2beta22 (2011-07-01)</b>

<ul><li>Includes LZO 2.05, replacing 2.03.</li></ul>

<ul><li>Sleep/wake change: When the computer wakes up, it now tries to reconnect all configurations that were connected, or were in the process of being connected, when it went to sleep. (Previously, Tunnelblick only tried to reconnect only those configurations that were connected when the computer went to sleep.)</li></ul>

<ul><li>Added an additional layer of protection against attacks.</li></ul>

<ul><li>Fixes a bug that caused connection failures for configurations on remote volumes or using shadow copies.</li></ul>

<ul><li>Fixes a bug that caused .tblk configurations on remote volumes or using shadow copies to ask for an administrator username/password each time a connection attempt was made.</li></ul>

<ul><li>Fixes a bug that didn't localize some window text.</li></ul>

<ul><li>Fixes a bug when using Set nameserver that caused domain/search name to be cut off.</li></ul>

<ul><li>Fixes a bug that caused shadow copies of configuration files to not be renamed, duplicated, removed, shared, or made private.</li></ul>

<ul><li>Fixes a bug that failed to remove some credentials when a configuration was removed.</li></ul>

<hr />

<b>3.2beta20 (2011-06-29)</b>

<ul><li>Fixes a bug causing domains to be ignored when 'Set nameserver' is selected.</li></ul>

<hr />

<b>3.2beta18 (2011-06-27)</b>

<ul><li>Fixes problems with sounds "on connect" and "on unexpected disconnect":<br>
<ul><li>Shows default sounds as "None".<br>
</li><li>Changes to the sound settings take effect immediately.</li></ul></li></ul>

<ul><li>Shows a splash screen during installation.</li></ul>

<ul><li>Cascades status windows when multiple status windows are being displayed simultaneously.</li></ul>

<ul><li>Monitors log only when it is being displayed.</li></ul>

<ul><li>Changes 'Connection window' to 'Notification window' on the Appearance panel of the 'VPN Details…' window.</li></ul>

<ul><li>Makes the log non-editable.</li></ul>

<ul><li>Enables Apple help instead of browser-based help when running on Snow Leopard.</li></ul>

<ul><li>Sorts configurations and sounds numerically (e.g., config2, config4, config35 instead of config2, config35, config4).</li></ul>

<ul><li>Minimizes CPU usage at high OpenVPN verb levels.</li></ul>

<ul><li>Streamlines the share/make private dialog.</li></ul>

<ul><li>Fixes problems displaying the 'VPN Details…' window when there are no configurations.</li></ul>

<ul><li>Fixes a problem that displayed incorrect sound 'on connect' and 'on unexpected disconnect' selections when no selections have been made. (Should have displayed 'None' for each, but displayed 'Glass' and 'Basso'.)</li></ul>

<ul><li>Fixes bug causing 100% CPU utilization when an unexpected error occurs while exiting the program.</li></ul>

<ul><li>Fixes problems renaming a configuration which is in a subfolder.</li></ul>

<ul><li>Fixes a small memory leak when the 'Show/Hide on Tunnelblick Menu' item is clicked.</li></ul>

<ul><li>Fixes a small memory leak when the VPN login window is shown.</li></ul>

<ul><li>Fixes a small memory leak when the 'Advanced' button on the 'Settings' tab of the 'Configurations' pane is clicked.</li></ul>

<hr />

<b>3.2beta16 (2011-06-24)</b>

<ul><li>Portuguese localization by Denis Volpato Martins. Thanks!</li></ul>

<ul><li>Includes a single up/down script pair for Set nameserver which works for both tun and tap devices. Thanks to Nick Williams!</li></ul>

<ul><li>Implements a new simplified menu, which moves all options and preferences to a new 'VPN Details…' window.</li></ul>

<ul><li>The new 'VPN Details…' window:<br>
<ul><li>Allows easy management of configurations, including renaming, duplicating, and removing them, and the ability to remove a configuration's credentials from the Keychain.<br>
</li><li>Includes a new GUI for modifying configuration settings, program preferences, and the appearance of the Tunnelblick icon and menu.</li></ul></li></ul>

<ul><li>Optionally plays a sound when the connection is completed or unexpectedly terminated or restarted.</li></ul>

<ul><li>Implements a new facility for installing configurations at the time Tunnelblick is installed, and updating them at any time thereafter.<br>
<ul><li>Installation of these configurations is triggered by including them in 'Tunnelblick Configurations.bundle' in Tunnelblick.app/Contents/Resources/. Thus they can be distributed as part of the normal Tunnelblick update mechanism.<br>
</li><li>The configurations are 'Tunnelblick VPN Configurations' (.tblk packages) and include all the options such configurations provide.<br>
</li><li>The configurations may be updated automatically, separate from the application.<br>
</li><li>Configuration updates (like Tunnelblick updates) must be digitally signed, or be transmitted over an SSL connection.<br>
</li><li>Configuration updates do not modify Tunnelblick.app, so they do not require modifying the digital signature of Tunnelblick.app.<br>
</li><li>The 'Tunnelblick Configurations.bundle' includes Info.plist entries that specify a URL for checking for and obtaining updates.</li></ul></li></ul>

<ul><li>Includes sample code for a VPN service provider to allow signup for service from a Tunnelblick menu command. This includes several screens stepping the user through acceptance of terms of service, password assignment, etc. an interacts with a service provider's webserver. It is implemented as a compile-time option, turned off in the source code at present. (This was developed for a VPN service provider, but is being released in generic form under the GPL as a part of Tunnelblick.)</li></ul>

<ul><li>Implements a new 'universal login' facility that allows a single username/password combination stored in the Keychain to be used for all configurations that do not have a separate username/password combination in the Keychain. This facility was designed to be used by the above VPN service provider signup code (although it does not presently use it).</li></ul>

<ul><li>Fixes problem with Tunnelblick icon not appearing in security dialogs.</li></ul>

<ul><li>Fixes problem displaying help on Snow Leopard.</li></ul>

<ul><li>Fixes problem with displaying logs for multiple configurations.</li></ul>

<ul><li>Implements 'reset all warnings' better.</li></ul>

<ul><li>Includes additional protection against symlink attacks.</li></ul>

<hr />

<b>3.2beta14 (2011-05-17)</b>

<ul><li>Fixes a crash on startup on OS X 10.4 ("Tiger") and 10.5 ("Leopard").</li></ul>

<ul><li>Fixes a typo in the help page for the "Appearance" preferences.</li></ul>

<hr />

<b>3.2beta12 (2011-05-16)</b>

<ul><li>Tunnelblick has a window for preferences. Configuration settings are still modified on the 'Details…' window.</li></ul>

<ul><li>Tunnelblick optionally displays a new, animated 'connecting' window as a configuration is being connected or reconnected. When the connection succeeds the window disappears. Display of the window is controlled by a preference which is set in the new preference window.</li></ul>

<ul><li>Menu streamlining:<br>
<ul><li>The 'Options…' submenu has been replaced by the 'Preferences…' item.<br>
</li><li>The top line of the menu now allows the user to 'Disconnect All' configurations. It continues to display the number of active connections, and, if there is only one active connection, now displays the name of that connection.<br>
</li><li>The 'Details…' menu item has been renamed to 'VPN Details…'.<br>
</li><li>The 'Disconnect…' menu items now optionally display connection times.<br>
</li><li>The 'Add a Configuration…' menu item has been renamed to "Add a VPN…" and moved from the 'Options…' submenu to the main menu.</li></ul></li></ul>

<ul><li>Preferences changes:<br>
<ul><li>Most preference changes take effect immediately; none require relaunching Tunnelblick.<br>
</li><li>The keyboard shortcut may be any of Command-Option-F1 through Command-Option-F12.<br>
</li><li>The 'skipWarningAboutNoTunOrTap' preference has been renamed to '-skipWarningAboutNoTunOrTap' (it was missing the '-').<br>
</li><li>Preferences are now stored in ~/Library/Application Support/Preferences/net.tunnelblick.tunnelblick.plist (because Tunnelblick's CFBundleIdentifier is now 'net.tunnelblick.tunnelblick'). The existing preferences file is renamed appropriately and a symbolic link to the new preferences file is put in its place when this version of Tunnelblick is first launched.</li></ul></li></ul>

<ul><li>Adds digital signatures to Tunnnelblick.app so that the popups each time Tunnelblick is updated that ask whether Tunnelblick can access the Keychain will no longer appear (after they do for this update). Note: this only works on OS 10.5 ("Leopard") and above.</li></ul>

<ul><li>A symbolic link at ~/Library/openvpn that does not point to ~/Library/Application Support/Tunnelblick no longer forces Tunnelblick to quit. Instead, a warning is issued in the Console log.</li></ul>

<ul><li>The 'VPN Details…' window has a minimum sizeto avoid a problem with OS X changing the button layout.</li></ul>

<ul><li>Fixes a bug that caused Tunnelblick to display the icon animation even though a user has requested that a connection attempt be cancelled after authentication fails.</li></ul>

<ul><li>Fixes a bug that caused the tooltip for the Tunnelblick icon and the status message (the first line of the menu exposed when you click the Tunnelblick icon) to display the wrong number of connections.</li></ul>

<ul><li>Fixes mislabeling of menu 'connection' items to clarify that they may be disconnected at any time they are not already disconnected.</li></ul>

<ul><li>Fixes a bug that caused 'Set nameserver (alternate 1)' to fail for some TAP connections.</li></ul>

<ul><li>Fixes a bug that did not allow Tunnelblick to launch on some OS X 10.4 ('Tiger') installations.</li></ul>

<ul><li>Fixes problem (since 3.2beta08) that user cannot set a configuration to connect or not connect when the computer starts. Note: configurations already set to start when the computer starts continued to work; this bug only affected trying to change a configuration from/to connecting when the computer starts.</li></ul>

<b>If you build (compile) Tunnelblick:</b>
<ul><li>You should create a signing certificate with Common Name 'TunnelblickSigning' using Keychain Access (see instructions at <a href='http://developer.apple.com/library/mac/#documentation/Security/Conceptual/CodeSigningGuide/Procedures/Procedures.html#//apple_ref/doc/uid/TP40005929-CH4-SW1'>http://developer.apple.com/library/mac/#documentation/Security/Conceptual/CodeSigningGuide/Procedures/Procedures.html#//apple_ref/doc/uid/TP40005929-CH4-SW1</a>). A certificate with that Common Name will be used automatically by the build scripts. If it is not present, no signing will take place and warnings will be issued during the build process.</li></ul>

<ul><li>Warnings during the build process that a target is already signed may appear if building the application but not rebuilding that particular target. These warnings may be ignored.</li></ul>

<hr />

<b>3.2beta10 (2011-04-29)</b>

<ul><li>Includes OpenVPN 2.2 and PKCS#11 1.08.</li></ul>

<ul><li>Includes complete Portuguese localization by Denis Volpato Martins. Thanks, Denis!</li></ul>

<ul><li>Removes the 'Clear log' button from the Details… window. (It is no longer needed because the log display is cleared at the start of each connection and its size is limited to 100,000 characters. This limit can be overridden by the 'maxLogDisplaySize' preference.).</li></ul>

<ul><li>Uses much less CPU time processing the log at high 'verb' levels.</li></ul>

<ul><li>Fixes bug that failed to properly deal with NetBIOSName when monitoring the connection.</li></ul>

<ul><li>Fixes bug that sometimes caused kexts to not be unloaded.</li></ul>

<ul><li>Fixes bugs when using  TAP, DHCP, and 'Set nameserver (alternate 1)'</li></ul>

<ul><li>Fixes bugs causing the connection time display to freeze.</li></ul>

<ul><li>Adds messages to the Console log that invalid user-supplied values are being ignored (usually preference values or Info.plist entries).</li></ul>

<hr />

<b>3.2beta08 (2011-04-26)</b>

<ul><li>No longer uses the down-root plugin if there are no 'user' or 'group' options in the configuration file. (The 'XXX-useDownRootPlugin' preference is removed in this situation.)</li></ul>

<ul><li>'Monitor connection' is more tolerant of unimportant changes and is more flexible:<br>
<ul><li>Allows scutil's output keys to be in any order.<br>
</li><li>Only monitors DomainName, ServerAddresses, and SearchDomains for DNS and NetBIOSName, Workgroup, and WINSAddresses for WINS/SMB.<br>
</li><li>New per-configration preference 'XXX-leasewatchOptions' (where XXX is the name of the configuration) consists of '-i' followed by the letters d, a, s, n, g, w to ignore the DomainName, ServerAddresses, SearchDomains, NetBIOSName, Workgroup, and WINSAddresses, respectively. If not present, all items are monitored. Example: to ignore all WINS/SMB changes, use '-ingw' (without the quotation marks).<br>
</li><li>New 'Set nameserver (3.1)' setting allows use of older 'Set nameserver' scripts.</li></ul></li></ul>

<ul><li>Higher 'verb' levels may be used without performance degradation:<br>
<ul><li>Tunnelblick doesn't process log files until you view the log in the Details… window. So you can capture the log using high verb levels, disconnect, and then view the last 10,000 lines (approximately) of the log in Tunnelblick. If you need access to the entire log, you can find it in the /Library/Application Support/Tunnelblick/Logs folder. The log is overwritten each time you connect, and is deleted when Tunnelblick exits.<br>
</li><li>Tunnelblick only tries to load the last 1,000,000 characters of the log file, so long log files don't take a long time to process.<br>
</li><li>Tunnelblick rate-limits queueing of notifications when the log file changes.<br>
</li><li>Tunnelblick 'chunks' additions to the log display.<br>
</li><li>The log is cleared before each connection attempt is made.</li></ul></li></ul>

<ul><li>Fixes bug that caused Tunnelblick to not connect 'automatically connect on launch' configurations. (The bug was apparently introduced in 3.2beta04.)</li></ul>

<ul><li>Fixes bug that sometimes causes retry of VPN username/password or passphrase to fail.</li></ul>

<ul><li>Fixes a bug that could cause an inability to start Tunnelblick because the installer was unable to properly secure it.</li></ul>

<hr />

<b>3.2beta06 (2011-04-06)</b>

<ul><li>Allows copy/paste of usernames, passwords, and passphrases in the VPN login window. (For security reasons, passwords and passphrases may only be pasted.)</li></ul>

<ul><li>Fixes a bug that sometimes failed to alert the user when a VPN username/password or passphrase failed to be authenticated, making it work better with some OpenVPN servers. (There is still a bug in OpenVPN which causes Tunnelblick to fail to report some failures; this bug is fixed in OpenVPN 2.2rc, which Tunnelblick betas will start using 'soon'.)</li></ul>

<ul><li>Allows Tunnelblick VPN Configurations ('.tblk' packages) to be uninstalled. If a Tunnelblick VPN Configuration is double-clicked and the 'TBUninstall' key is included in its Info.plist (with any value), the installed configuration that has corresponding attributes (install location, bundle ID) will be uninstalled. If the key is the string 'ignoreError' (without the quote marks), any failures in the uninstall process will not be reported to the user.</li></ul>

<ul><li>Allows the deletion of backups of the Deploy folder by installing a version of Tunnelblick.app which includes an empty /Contents/Resources/Deploy folder. (This allows a user to install a fresh un-Deployed Tunnelblick over a Deployed version.)</li></ul>

<ul><li>Moves LeaseWatch.plist to /Library/Application Support/Tunnelblick so Tunnelblick.app is not modified (thus preserving the validity of the application's digital signature, if any).</li></ul>

<ul><li>Adds translations of additional OpenVPN connection status.</li></ul>

<ul><li>Includes changes to avoid two false-positive Xcode 3.2.5 analyzer warnings in NetSocket.m.</li></ul>

<ul><li>Fixes a bug that sometimes caused unnecessary 'The change will take effect the next time you connect' messages.</li></ul>

<ul><li>Fixes a bug that sometimes caused Tunnelblick to be unable to establish communications with OpenVPN.</li></ul>

<ul><li>Fixes a bug that sometimes -- on OS X 10.4 ('Tiger') only -- caused Tunnelblick to hang while quitting or connecting to a VPN server.</li></ul>

<ul><li>Fixes a problem that installed nested Tunnelblick VPN Configurations (.tblk packages) incorrectly.</li></ul>

<ul><li>Fixes a bug that caused Tunnelblick to refuse to install Tunnelblick VPN Configurations if they contained subfolders.</li></ul>

<ul><li>Fixes a bug that caused a Console log entry that a flag file does not exist after installing certain Tunnelblick VPN Configurations (.tblk).</li></ul>

<ul><li>Fixes a bug that caused tun/tap kexts to be loaded even though preferences specify that the kext(s) are not to be loaded.</li></ul>

<hr />

<b>3.2beta04 (2011-02-19)</b>

<ul><li>Adds <a href='cAppleScriptSupport.md'>AppleScript support</a>.</li></ul>

<ul><li>Includes complete French localization by Jeremy W. Sherman. Thanks, Jeremy!</li></ul>

<ul><li>Includes OpenSSL 1.0.0d.</li></ul>

<ul><li>Unloading of the foo.tap and foo.tun kexts is now attempted only if they are already loaded (previously, it was always attempted and errors were ignored).</li></ul>

<ul><li>Fixes problems with fast user switching (previously, user switches were ignored, which caused problems if Tunnelblick was used by more than one user and could cause the icon to indicate no VPN connection when one existed):<br>
<ul><li>When a user is switched out, all configurations that are not set to "connect when computer starts" will be disconnected unless the per-connection "-doNotDisconnectOnFastUserSwitch" preference is set true.<br>
</li><li>When a user is switched in, Tunnelblick will attempt to connect any configurations that were connected at the time the user was switched out but are no longer connected unless the per-connection "-doNotReconnectOnFastUserSwitch" preference is set true.</li></ul></li></ul>

<ul><li>Fixes potential race condition when computer wakes up.</li></ul>

<ul><li>Fixes bug that can cause unnecessary warnings about unknown OpenVPN processes.</li></ul>

<ul><li>Fixes bug that caused up/down scripts in .tblks to not be executed.</li></ul>

<ul><li>Fixes bug that can cause crashes after connecting to a VPN.</li></ul>

<hr />

<b>3.2beta02 (2011-02-02)</b>

<ul><li>The following scripts may be included in a Tunnelblick VPN Configuration (.tblk package):<br>
<ul><li>The 'pre-connect.sh' script is executed (as root) before Tunnelblick would unload and/or load the tun or tap kexts (whether or not any unload or load takes place).<br>
</li><li>The 'post-tun-tap-load.sh' script is executed (as root) after Tunnelblick unloads and/or loads the tun or tap kexts (whether or not any unload or load takes place). Thus, the script is executed immediately before starting OpenVPN.<br>
</li><li>The 'connected.sh' script is executed (as root) when a configuration connects. This script is executed only if Tunnelblick is running at the time of the event, which may not be the case for 'when computer starts' configurations.<br>
</li><li>The 'reconnecting.sh' script is executed (as root) when OpenVPN loses the VPN connection and is trying to reconnect. This script is executed only if Tunnelblick is running at the time of the event, which may not be the case for 'when computer starts' configurations.<br>
</li><li>The 'post-disconnect.sh' script is executed (as root) after OpenVPN has closed the connection. This script is executed only if Tunnelblick is running at the time of the event, which may not be the case for 'when computer starts' configurations.</li></ul></li></ul>

<ul><li>Fixes problem installing Tunnelblick via double-click when the user's home folder is not on the same volume as /Applications/Tunnelblick.app</li></ul>

<ul><li>Warns the user if a configuration is set to to connect when the computer starts and it is a Tunnelblick VPN Configuration (.tblk package) which includes a 'connected.sh', 'reconnecting.sh', or 'post-disconnect.sh' script. Those scripts are not executed unless Tunnelblick itself is running when the event occurs, which may not be the case for 'when computer starts' configurations.</li></ul>

<ul><li>Tunnelblick (but not third-party) preparation for OS X 10.7 (Lion), including isolating deprecated methods and changes for GCC 4.2. Warnings about 'object file compiled with -mlong-branch' when building Tunnelblick are now <i>gone</i> -- building Tunnelblick generates warnings only for third-party software. (Still generates code for OS X 10.4, 10.5, and 10.6)</li></ul>

<ul><li>Fixes a few small memory leaks: one VPNConnection objects per sleep/wake cycle, two NSStrings per connect/disconnect, one NSMutableArray and two NSImages each time the "Use Original Icon" menu command is clicked, several objects each time executeAuthorized is run, and <a href='https://code.google.com/p/tunnelblick/issues/detail?id=171'>Issue 171</a>.</li></ul>

<ul><li>Removed 5 second delay before launching Tunnelblick after installation</li></ul>

<ul><li>Removed references to "intValueOfBuildForBundle" because it is no longer used</li></ul>

<ul><li>Updated copyright notices and added Free Software Foundation license URL</li></ul>

<hr />

<h2>Version 3.1</h2>

<hr />

<b>3.1.7 (2011-04-03)</b>

<ul><li>Fixes problems causing tun/tap kexts to be loaded even though preferences specify that the kext(s) are not to be loaded.<br>
</li><li>Fixes a problem with installing some Tunnelblick VPN Configurations (.tblk).</li></ul>

<hr />

<b>3.1.6 (2011-02-19)</b>

<ul><li>Fixes a bug that caused up/down scripts in Tunnelblick VPN Configurations (.tblks) to be ignored.</li></ul>

<hr />

<b>3.1.5 (2011-02-01)</b>

<ul><li>Fixes a bug causing installation/repair failures on OS X 10.4 ("Tiger") PPC.</li></ul>

<hr />

<b>3.1.4 (2011-01-28)</b>

<ul><li>Fixes a bug causing installation/repair failures on OS X 10.4 ("Tiger").</li></ul>

<hr />

<b>3.1.3 (2011-01-27)</b>

<ul><li>Fixes a security vulnerability which affects all earlier Tunnelblick 3.1 versions (but not any 3.0 versions).</li></ul>

<ul><li>Adds a 'Use Original Icon' item to the 'Options' menu to allow easy switching between the original grayscale Tunnelblick icon and the new yellow-light-at-the-end-of-the-tunnel Tunnelblick icon.</li></ul>

<blockquote>This menu item is not displayed:<br>
<ul><li>If the 'doNotShowUseOriginalIconMenuItem' preference item exists and is true; or<br>
</li><li>If Tunnelblick.app/Contents/Resources/IconSets/TunnelBlick-black-white.TBMenuIcons does not exist; or<br>
</li><li>If the 'menuIconSet' preference exists and contains anything other than 'TunnelBlick.TBMenuIcons' or 'TunnelBlick-black-white.TBMenuIcons'.</li></ul></blockquote>

<ul><li>Displays "(Private)", "(Shared)", or "(Deployed)" after a configuration name only if more than one type of configuration is present.</li></ul>

<ul><li>Warns (in the Console log) about missing or incomplete icon sets and attempts to use the standard icon set.</li></ul>

<ul><li>Fixes a bug that sometimes misinterpreted the configuration file causing a "No 'dev tun' or 'dev tap' found" warning to appear even when such an option did appear in the configuration file.</li></ul>

<ul><li>Fixes a bug that sometimes caused the warning that "OpenVPN is not responding to disconnect requests" to appear when OpenVPN had already responded to a disconnection request.</li></ul>

<ul><li>Fixes bugs that sometimes caused Tunnelblick icon to show the "connecting" animation even though a connection attempt has been completed successfully or abandoned, or after abandoning an attempt to hook up to an existing OpenVPN process.</li></ul>

<ul><li>Fixes a bug that sometimes caused logging to be disabled if the openvpn-down-root.so plugin were used.</li></ul>

<ul><li>Fixes a bug that caused a warning that there are no configurations during the process of updating a "Deployed" version of Tunnelblick.</li></ul>

<ul><li>Fixes a bug that could cause Tunnelblick to hang during installation from a disk image. (Not likely to ever happen, though!)</li></ul>

<hr />

<b>3.1.2 (2010-12-25)</b>

<ul><li>Removes the 'warns the user when certain unexpected disconnections occur' feature added in version 3.1.1 because it caused Tunnelblick to hang under certain conditions of sleep/wake cycles and/or screensavers. This feature will return in more robust form in a future beta release.</li></ul>

<hr />

<b>3.1.1 (2010-12-18)</b>

<ul><li>Fixes a problem with the left navigation sometimes not being displayed properly when the Details… window does not have left navigation but adding a configuration changes it to have left navigation.</li></ul>

<ul><li>Fixes a problem installing Tunnelblick VPN Configurations (.tblk packages) that have a CFBundleIdentifier containing upper-case letters.</li></ul>

<ul><li>Fixes a problem when a .tblk that is being installed has a path which includes a component which includes the string '.tblk'</li></ul>

<ul><li>Fixes a problem checking permissions on configuration file when user's home folder is not the usual /Users/username folder -- for example, when it is on a network volume (<a href='https://code.google.com/p/tunnelblick/issues/detail?id=163'>Issue 163</a>).</li></ul>

<ul><li>Fixes a problem with the Tunnelblick icon not displaying correctly for multiple simultaneous connections. Now the icon is a closed tunnel if all configurations that the user expects to be closed are in fact closed, is an open tunnel if all configurations that the user expects to be open are in fact open; otherwise the icon is an animation -- neither open nor closed.</li></ul>

<ul><li>Fixes a problem trying to set a configuration that is in a subfolder to connect at system start.</li></ul>

<ul><li>Fixes openvpnstart crashes when certain errors occurred. (Tunnelblick itself did not crash.)</li></ul>

<ul><li>Fixes problems when using 'shadow' configuration files.</li></ul>

<ul><li>Warns the user when certain unexpected disconnections occur.</li></ul>

<ul><li>Adds a message to the OpenVPN log displayed in the Details… window when Tunnelblick obtains a VPN passphrase or username/password from the Keychain.</li></ul>

<ul><li>Waits to go to sleep until all OpenVPN processes have terminated, unless the 'doNotPutOffSleepUntilOpenVPNsTerminate' boolean preference is set true.</li></ul>

<ul><li>Changes Tunnelblick icon animation and open tunnel icon to show yellow beyond the tunnel, brightening the icon subtly. To use the old icon animation, set the 'menuIconSet' preference to the string 'TunnelBlick-black-white.TBMenuIcons'. Many thanks to Wes Plate for this new icon set.</li></ul>

<ul><li>Fixes the inability to display the build number when the Tunnelblick version number that has a period in the build number (as do these 3.1.1 builds).</li></ul>

<ul><li>Fixes a typographical error in an error message referring to a known problem in OpenVPN 2.1 -- the error message incorrectly referred to OpenVPN 2.2.</li></ul>

<hr />

<b>3.1 (2010-12-05)</b>

<ul><li>Only the version and build numbers were updated.</li></ul>

<hr />

<b>3.1beta24 (2010-12-03)</b>

<ul><li>Updates to use OpenSSL 1.0.0c, which fixes several security vulnerabilities.</li></ul>

<ul><li>Searches for the icon set folder in Tunnelblick.app/Contents/Resources/Deploy and then in /Library/Application Support/Tunnelblick/Shared before defaulting to the version in Tunnelblick.app/Contents/Resources.</li></ul>

<ul><li>Fixes bug that caused an unneeded folder (dmgFiles) to be built into Tunnelblick.app/Contents/Resources.</li></ul>

<hr />

<b>3.1beta22 (2010-12-01)</b>

<ul><li>Updated to include OpenVPN 2.1.4 and OpenSSL 1.0.0b.</li></ul>

<ul><li>Adds a note to the OpenVPN log (in the Details… window) when the computer goes to sleep or wakes up and a connection is terminated/restarted.</li></ul>

<ul><li>Fixes a problem modifying 'Set nameserver' on other-than-the-first connection.</li></ul>

<ul><li>Fixes an OpenVPN problem with special case route targets ('remote_host')</li></ul>

<hr />

<b>3.1beta20 (2010-10-31)</b>

<ul><li>Removed confusing question when Tunnelblick is launched and foo.tap and/or foo.tun (old Tunnelblick kexts) are loaded. The question asked if foo.tun and foo.tap should be unloaded. Now they are unloaded only as needed to make a connection: foo.tap is unloaded if net.tunnelblick.tap is being loaded for the connection, and foo.tun is unloaded if net.tunnelblick.tun is being loaded for the connection. The 'skipAskingToUnloadFooKexts' preference is no longer used. To override Tunnelblick's automatic loading of the tun or tap kexts required for a connection, see the following per-configuration <a href='wPrefs.md'>Preferences</a>: "-doNotLoadTunKext", "-doNotLoadTapKext", "-loadTunKext", and "-loadTapKext".</li></ul>

<hr />

<b>3.1beta18 (2010-010-16)</b>
<ul><li>When there are more than eight configurations, the Details… window changes to display a list of connections on the left side and a single tab with the log and controls on the right. This was done because of OS X problems when there are a large numbers of tabs. The 'maximumNumberOfTabs' preference specifies the maximum number of tabs to display; if there are more than that many configurations, the display will change as described above. The preference defaults to 8. Set this preference to 0 to always show configurations in a list on the left.</li></ul>

<ul><li>Streamlines installation by double-clicking to have only one dialog box explaining what will be installed and asking for admin username/password.</li></ul>

<ul><li>Fixes bug which prevented Standard users from installing Tunnelblick by double-clicking.</li></ul>

<ul><li>Fixes bugs in automatic installation of .tblks when installing Tunnelblick.</li></ul>

<hr />

<b>3.1beta16 (2010-010-08)</b>
<ul><li>Replaces the 'Set nameserver' checkbox with a drop-down list that can display additional choices to allow different up/down scripts to be used.<br>
<ul><li>The following choices will always be displayed:<br>
<ul><li>'Do not set nameserver' to not use any scripts                  (equivalent to not having a check in the old 'Set nameserver' checkbox')<br>
</li><li>'Set nameserver'        to use the standard Tunnelblick scripts (equivalent to having a check in the old 'Set nameserver' checkbox')<br>
</li></ul></li><li>The following two additional choices will be displayed only if custom scripts are not being used:<br>
<ul><li>'Set nameserver (3.0b10)'      to use scripts from Tunnelblick 3.0b10 (for backward compatibility)<br>
</li><li>'Set nameserver (alternate 1)' to use scripts based on Ben Low's scripts from <a href='http://openvpn.net/archive/openvpn-users/2006-10/msg00120.html'>http://openvpn.net/archive/openvpn-users/2006-10/msg00120.html</a>. These scripts:<br>
<ul><li>Implement multiple domains 'pushed' from the server<br>
</li><li>Fix some issues with some TAP connections that cause 'write to TUN/TAP : Input/output error (code=5)' and other errors<br>
</li><li>Do not implement 'Monitor connection'<br>
</li></ul></li></ul></li><li>Note: Some Deployed versions of Tunnelblick and Tunnelblick VPN configurations may include custom scripts that will inhibit the display of these two additional choices.<br>
</li><li>Running this version changes the 'useDNS' per-configuration preference from a boolean to a number. This is a downward-compatible change -- earlier versions of Tunnelblick may be run after running this version and modifying the 'Set nameserver' selection. The earlier version will consider anything other than 'Do not set nameserver' as if the 'Set nameserver' checkbox were checked.<br>
</li><li>Warning: If Build 2054 changes the setting to 'Set nameserver (3.0b10)' or 'Set nameserver (alternate 1)', using an earlier version of Tunnelblick to modify the checkbox so it is checked will revert the setting back to 'Set nameserver'.</li></ul></li></ul>

<ul><li>Adds the ability to add menu items to the Tunnelblick menu to execute programs (e.g., scripts).<br>
</li><li>Adds the ability to specify programs that should be executed when Tunnelblick is launched or when a connection is attempted.<br>
</li></ul><blockquote>(See <a href='cCusDeployed#Additional_Menu_Commands_and_Programs.md'>Additional Menu Commands and Programs</a> for details.)</blockquote>

<ul><li>Includes localization-related code tweaks by Stefan Bethke and additional German localization by Stefan Bethke, Marcus Schneider, and 'Dr Hok'.</li></ul>

<ul><li>Fixes a formatting error when displaying file permissions in error messages about being unable to change permissions.</li></ul>

<ul><li>Fixes a problem causing a connection restart when 'Set nameserver' is used, a DHCP renewal occurs, and there are no WINS settings.</li></ul>

<ul><li>Fixes issues when using OpenDirectory and the user's home directory is on a non-Mac platform.</li></ul>

<hr />

<b>3.1beta14 (2010-09-09)</b>
<ul><li>Fixes <a href='https://code.google.com/p/tunnelblick/issues/detail?id=159'>Issue 159</a> problem that, under certain circumstances, crashes client.down.tunnelblick.sh</li></ul>

<ul><li>Includes OpenVPN version 2.1.3.</li></ul>

<ul><li>Thanks to Mohammad A. Haque: Includes the OpenSSL v. 1.0.0a library imbedded into the included OpenVPN binary. This adds support for the following:</li></ul>

<blockquote>Digests:<br>
<blockquote>ecdsa-with-SHA1 160 bit digest size<br>
MD2 128 bit digest size<br>
RSA-MD2 128 bit digest size<br>
RSA-SHA224 224 bit digest size<br>
RSA-SHA256 256 bit digest size<br>
RSA-SHA384 384 bit digest size<br>
RSA-SHA512 512 bit digest size<br>
SHA224 224 bit digest size<br>
SHA256 256 bit digest size<br>
SHA384 384 bit digest size<br>
SHA512 512 bit digest size<br>
whirlpool 512 bit digest size<br></blockquote></blockquote>

<blockquote>Ciphers:<br>
<blockquote>CAMELLIA-128-CBC 128 bit default key (fixed)<br>
CAMELLIA-128-CFB 128 bit default key (fixed)<br>
CAMELLIA-128-CFB1 128 bit default key (fixed)<br>
CAMELLIA-128-CFB8 128 bit default key (fixed)<br>
CAMELLIA-128-OFB 128 bit default key (fixed)<br>
CAMELLIA-192-CBC 192 bit default key (fixed)<br>
CAMELLIA-192-CFB 192 bit default key (fixed)<br>
CAMELLIA-192-CFB1 192 bit default key (fixed)<br>
CAMELLIA-192-CFB8 192 bit default key (fixed)<br>
CAMELLIA-192-OFB 192 bit default key (fixed)<br>
CAMELLIA-256-CBC 256 bit default key (fixed)<br>
CAMELLIA-256-CFB 256 bit default key (fixed)<br>
CAMELLIA-256-CFB1 256 bit default key (fixed)<br>
CAMELLIA-256-CFB8 256 bit default key (fixed)<br>
CAMELLIA-256-OFB 256 bit default key (fixed)<br>
DES-EDE3-CFB1 192 bit default key (fixed)<br>
DES-EDE3-CFB8 192 bit default key (fixed)<br>
IDEA-CBC 128 bit default key (fixed)<br>
IDEA-CFB 128 bit default key (fixed)<br>
IDEA-OFB 128 bit default key (fixed)<br>
RC5-CBC 128 bit default key (variable)<br>
RC5-CFB 128 bit default key (variable)<br>
RC5-OFB 128 bit default key (variable)<br>
SEED-CBC 128 bit default key (fixed)<br>
SEED-CFB 128 bit default key (fixed)<br>
SEED-OFB 128 bit default key (fixed)<br></blockquote></blockquote>

<blockquote>TLS Ciphers:<br>
<blockquote>CAMELLIA128-SHA<br>
CAMELLIA256-SHA<br>
DHE-DSS-CAMELLIA128-SHA<br>
DHE-DSS-CAMELLIA256-SHA<br>
DHE-DSS-SEED-SHA<br>
DHE-RSA-CAMELLIA128-SHA<br>
DHE-RSA-CAMELLIA256-SHA<br>
DHE-RSA-SEED-SHA<br>
ECDH-ECDSA-AES128-SHA<br>
ECDH-ECDSA-AES256-SHA<br>
ECDH-ECDSA-DES-CBC3-SHA<br>
ECDH-ECDSA-RC4-SHA<br>
ECDH-RSA-AES128-SHA<br>
ECDH-RSA-AES256-SHA<br>
ECDH-RSA-DES-CBC3-SHA<br>
ECDH-RSA-RC4-SHA<br>
ECDHE-ECDSA-AES128-SHA<br>
ECDHE-ECDSA-AES256-SHA<br>
ECDHE-ECDSA-DES-CBC3-SHA<br>
ECDHE-ECDSA-RC4-SHA<br>
ECDHE-RSA-AES128-SHA<br>
ECDHE-RSA-AES256-SHA<br>
ECDHE-RSA-DES-CBC3-SHA<br>
ECDHE-RSA-RC4-SHA<br>
IDEA-CBC-SHA<br>
PSK-3DES-EDE-CBC-SHA<br>
PSK-AES128-CBC-SHA<br>
PSK-AES256-CBC-SHA<br>
PSK-RC4-SHA<br>
SEED-SHA<br></blockquote></blockquote>

<blockquote>For a complete list of available digests, ciphers, and TLS ciphers, type the following into Terminal:<br>
<pre><code>    sudo ./openvpn --show-digests --show-ciphers --show-tls<br>
</code></pre></blockquote>

<blockquote>("sudo" is needed if Tunnelblick.app has been run at least once, because Tunnelblick secures the OpenVPN binary by making it owned and executable only by root.)</blockquote>

<hr />

<b>3.1beta12 (2010-08-08)</b>
<ul><li>Includes Italian localization thanks to Pierpaolo Gulla (Grazie!).</li></ul>

<ul><li>Implements a single, system-wide keyboard shortcut (command-option-F1 by default) to expose the Tunnelblick menu.<br>
<ul><li>This make it possible to use Tunnelblick with only a keyboard.<br>
</li><li>The keyboard shortcut may be used whenever Tunnelblick is running - it does not need to be the front-most application.<br>
</li><li>A new submenu of the Options submenu has been added to allow the key to be changed to any of the function keys from F1 through F12. The display of the new submenu is inhibited if the 'doNotShowKeyboardShortcutSubmenu' preference is set to TRUE.<br>
</li><li>Two new unsigned integer preferences: 'keyboardShortcutKeyCode' contains the virtual keycode for the key, and 'keyboardShortcutModifiers' contains the code for the modifier keys.</li></ul></li></ul>

<ul><li>No longer displays Tooltips by default. They are displayed only if the 'showTooltips' preference is set to TRUE. This is necessary because tooltips on menu items interfere with the proper operation of VoiceOver, OS X's built-in screen access solution.</li></ul>

<ul><li>Terminates faster if going to sleep or if no unknown OpenVPN processes exist and no 'when computer starts' configurations are connected.</li></ul>

<ul><li>Works around the following OpenVPN bug: when in the 'RESOLVE' state, the OpenVPN process ignores the first SIGTERM (via kill or management interface) and delays termination for tens of seconds after a second or subsequent SIGTERM. Works around this by warning the user that this is happening, then repeatedly sending SIGTERM and, after a timeout period (default is 180 seconds), considering the connection closed even if OpenVPN doesn't acknowledge the closing. Two new preferences specify the time in seconds between sending SIGTERMs ('openvpnTerminationInterval') and the total maximum time in seconds to wait before considering the connection closed ('openvpnTerminationTimeout').</li></ul>

<ul><li>Logs errors trying to create or update 'Launch Tunnelblick' in the private configurations folder.</li></ul>

<ul><li>Fixes bugs (race conditions) when the log view is being updated and when MenuExtras are added.</li></ul>

<ul><li>Fixes bug with placement of the 'when computer starts' radio button in non-English versions of Tunnelblick.</li></ul>

<hr />

<b>3.1beta10 (2010-07-29)</b>
<ul><li>Configurations located in subfolders are displayed in submenus of the main Tunnelblick menu.</li></ul>

<ul><li>The 'wizard' that runs when there are no configurations present or when the user selects 'Add a configuration…' has been enhanced.</li></ul>

<ul><li>When there are no configurations available, two menu items are displayed in place of the configurations:  'No VPN Configurations Available' and 'Add a Configuration…'. (The 'Add a Configuration…' menu item will not be displayed if the 'doNotShowAddConfigurationMenuItem' preference is true.)</li></ul>

<ul><li>An 'Add a Configuration…' menu item was added to the 'Options…' submenu. (It will not be displayed if the 'doNotShowAddConfigurationMenuItem' preference is true.) This menu item starts the configuration wizard.</li></ul>

<ul><li>When a Tunnelblick VPN Configuration (.tblk package) is installed, all Tunnelblick VPN Configurations within it will be installed. If these 'inner' configurations are inside subfolders of the outer .tblk, they will be installed as subfolders of the configurations folders and will appear in submenus of the main Tunnelblick menu.</li></ul>

<ul><li>automatic installation of configurations from the .dmg has changed: Only one Tunnelblick VPN Configuration (.tblk packages) in the '.auto-install' or '.auto-install' folders and their subfolders is installed.</li></ul>

<ul><li>The ability to install Tunnelblick VPN Configurations from malformed folder contents has been improved.</li></ul>

<ul><li>Tunnelblick now tries up to five times to get the login items, avoiding a timing issue.</li></ul>

<ul><li>The log display in the Details… window is now read-only from the keyboard.</li></ul>

<ul><li>If it doesn't exist, Tunnelblick creates a symlink to ~/Library/Application Support/Tunnelblick/Configurations from ~/Library/openvpn. This avoids a problem when a user launches a new version of Tunnelblick one or more times without having ever used an older version, and then tries to use an older version.</li></ul>

<ul><li>Attempts to repair more configuration folder problems, such as the existence of both the old and new folders.</li></ul>

<ul><li>Fixes bugs in the shadow copy mechanism that caused connect failures, log-hookup failures, and (possibly) other problems. Thanks to Jim Bo for pointing out the first problem and suggesting a solution.</li></ul>

<ul><li>Fixes bug that caused tun/tap kexts to fail to unload when a connection was closed</li></ul>

<ul><li>Fixes incorrect help message for 'openvpnstart'</li></ul>

<hr />

<b>3.1beta08 (2010-07-10)</b>
<blockquote><font color='red'><b>IMPORTANT NOTE FOR THOSE USING "WHEN COMPUTER STARTS" WITH EARLY 3.1BETA VERSIONS:</b></font> The first time that you update to Tunnelblick 3.1beta08 or above from 3.1beta02 - 3.1beta06, Tunnelblick will not recognize any <b>running</b> "when computer starts" configurations. Five to ten seconds after you start Tunnelblick, they will be identified as unknown OpenVPN processes and you will be given the choice to leave them alone or disconnect them. You should chose to disconnect them in this dialog and then manually connect them in Tunnelblick. (You do not need to do this immediately, but you will not be able to control them with Tunnelblick. The dialog will appear each time you start Tunnelblick if these connections are still active.) This need only be done once, and is not necessary if there are no "when computer starts" configurations that are connected at the time you update.</blockquote>

<ul><li>Benji Greig has created an updated Tunnelblick icon that looks great in Coverflow. He has also created a distinctive icon for Tunnelblick VPN Configurations, and a new background image for the Disk Image. Thanks, Benji!</li></ul>

<ul><li>Log processing and display have been rewritten:<br>
<ul><li>OpenVPN log files are kept in /tmp/tunnelblick/logs using filenames encoded with the configuration file path, the management port number, and the arguments to openvpnstart when the connection was created.<br>
</li><li>Script log files are kept in the same directory, using filenames encoded with the configuration file path.<br>
</li><li>Log files are created each time a connection is made. 'Pipes' are no longer used for the script files, and the OpenVPN management interface is not used to process log data.<br>
</li><li>When displaying the log, the entries are merged such that script log entries follow OpenVPN log entries that have the same date/time.<br>
</li><li>The log display now shows the most recent 10000 entries. Earlier entries are not displayed, but they are available in the log files stored in /tmp/tunnelblick/logs.<br>
</li><li>Formatting of the log display is improved."</li></ul></li></ul>

<ul><li>The DNS cache is flushed after a tunnel is established and after it is torn down. This is enabled by default but may be disabled by the per-connection "-doNotFlushCache" preference.</li></ul>

<ul><li>Tunnelblick VPN Configurations (.tblk packages) may now be shadow copied</li></ul>

<ul><li>Configurations (.conf, .ovpn, and .tblk) may be stored in subfolders. Note that .tblk configurations are installed at the top level of the shared or private folder; they must then be moved to a subfolder if that is desired.</li></ul>

<ul><li>Sets share/private button to 'Share configuration' when it is disabled.</li></ul>

<ul><li>Fixes bug that caused 'Ignoring change of Network Primary Service' message to be displayed when no change occurred.</li></ul>

<ul><li>Fixes bug that caused unload of tun/tap kext at exactly the right time while a restart was taking place if the user disconnected a different configuration that used the same tun/tap kext.</li></ul>

<ul><li>Fixes bug that caused .conf configuration files to be ignored.</li></ul>

<ul><li>Fixes bug that caused failure to connect if "Monitor connection" was checked and the standard up script was used.</li></ul>

<ul><li>Fixes bug that caused restarts to fail if a different configuration was disconnected at exactly the right (or wrong!) time.</li></ul>

<ul><li>Fixes bug that didn't clean up when installation of a .tblk package failed.</li></ul>

<ul><li>Fixes bug that caused 'Set nameserver' script (i.e., 'leasewatch') to be run when it is not necessary.</li></ul>

<ul><li>Fixes bug that caused launch of leasewatch script (when 'Set nameserver' is checked) to fail if automatically connecting when computer starts</li></ul>

<ul><li>Fixes bug which causes format errors in the log display if a script generates log entries which don't have a "<code>*</code>" after the date/time. (Inserts a "<code>*</code>" in such entries in the log display.)</li></ul>

<hr />

<b>3.1beta06 (2010-06-07)</b>
<ul><li>Takes into account both the 'dev-type' and 'dev' options in the configuration file when trying to determine if it is a 'tun' or 'tap' connection. Tunnelblick tries to determine that so it can load only the tap or tun kext (device driver) that is required. Note: there appears to be a bug in OpenVPN that makes the dev-type option fail; this does not help that problem.</li></ul>

<ul><li>Runs new scripts, pre-connect.sh and post-disconnect.sh, as root before connecting and/or after disconnecting if the scripts exist. (They must be in a .tblk package). This allows manipulation of kexts and/or the network configuration before the tun/tap kexts are loaded and OpenVPN is run and after OpenVPN exits and the kexts are unloaded.</li></ul>

<ul><li>Changed "Online Documentation.webloc" that is put in the .dmg so it will go to the new main documentation page.</li></ul>

<ul><li>Fixes bug that caused .conf configuration files to be ignored.</li></ul>

<ul><li>Fixes bug that caused failure to connect if "Monitor connection" was checked and the standard up script was used.</li></ul>

<ul><li>Fixes bug that caused restarts to fail if a different configuration was disconnected at exactly the right (or wrong!) time.</li></ul>

<ul><li>Fixes bug that didn't clean up when installation of a .tblk package failed.</li></ul>

<hr />

<b>3.1beta04 (2010-05-27)</b>
<ul><li>Creates pipes for script output to "Details…" window on demand instead of when Tunnelblick launches</li></ul>

<ul><li>Deletes logs for 'when computer starts' connections when they are disconnected</li></ul>

<ul><li>Doesn't un-check 'Connect automatically' if administrator permission to change from 'when Tunnelblick launches' to 'when computer starts' is cancelled, so connect 'when Tunnelblick launches' will remain in effect</li></ul>

<ul><li>Allows cancel out of dialog asking if 'openvpn-down-root.so' should be used</li></ul>

<ul><li>Marks start and end of OpenVPN log entries from before Tunnelblick was launched</li></ul>

<ul><li>Displays a notice if then OpenVPN log entries from before Tunnelblick was launched are more than 10,000,000 bytes long.</li></ul>

<ul><li>Includes path of openvpnstart to be used in Console log messages that a configuration will 'connect when computer starts'</li></ul>

<ul><li>Reinforces security of openvpnstart -- it now verifies it is protected before doing any operations</li></ul>

<ul><li>Reformats dates in OpenVPN log entries from before Tunnelblick was launched to YYYY-MM-DD HH:MM:SS</li></ul>

<ul><li>A DHCP renew which restores the original DNS and/or WINS information no longer causes the connection to restart. This new behavior can reversed be by setting Tunnelblick the boolean preferences '-doNotRestoreOnDnsReset' and/or '-doNotRestoreOnWinsReset' to TRUE.</li></ul>

<ul><li>Modified the up, down, and leasewatch scripts:<br>
<ul><li>client.up.osx.s and client.nomonitor.up.osx.sh are replaced by client.up.tunnelblick.sh<br>
</li><li>client.down.osx.s and client.nomonitor.down.osx.sh are replaced by client.down.tunnelblick.sh<br>
</li><li>The up and down scripts may be called with optional arguments (before the standard OpenVPN-supplied arguments) that are prefixed by a '-'. The arguments are:<br>
<ul><li>-m to monitor the network configuration (reflects the 'Monitor connection' checkbox);<br>
</li><li>-w to cause restoration of expected WINS configuration if it changes to the pre-VPN configuration (via DHCP renewal, for example); and<br>
</li><li>-d to cause restoration of expected  DNS configuration if it changes to the pre-VPN configuration (via DHCP renewal, for example).<br>
</li></ul></li><li>The -w and -d options are specified if the boolean Tunnelblick preferences '-doNotRestoreOnDnsReset' and/or '-doNotRestoreOnWinsReset' are TRUE.<br>
</li><li>The up script saves, and leasewatch and the down script access, additional parameters (the state of the optional arguments, network primary service ID, and logfile path) in the System Configuration database as /Network/OpenVPN/...<br>
</li><li>The up script saves the pre-VPN WINS (SMB) configuration in the System Configuration database as /Network/OpenVPN/OldSMB<br>
</li><li>The down script ignores the optional arguments (accessing any it needs via the System Configuration database)<br>
</li><li>leasewatch behavior has changed, although a Tunnelblick preference restores the old behavior. It used to restart the connection if the DNS or WINS configuration changed from the post-VPN-creation configuration (which reflects 'pushed' values from the OpenVPN server). This caused a restart of the connection when a DHCP renewal changed the settings to the pre-VPN configuration. This situation is now detected, and the DNS and/or WINS configurations are restored to the post-VPN-creation configuration instead of restarting the connection. This new behavior may be inhibited (forcing the old behavior to restart the connection) by setting the boolean Tunnelblick preferences '-doNotRestoreOnDnsReset' and/or '-doNotRestoreOnWinsReset' to FALSE.<br>
</li><li>Tunnelblick itself has been modified to use the new scripts, but only if the old scripts are not present. That means that an automated build process, for example, which replaces client.up.osx.sh with a customized version, will continue to work, because Tunnelblick will see the old script, and use that instead of using the new script (even if the new script is present).<br>
</li><li>The openvpnstart 'bitMask' argument has additional bits that specify options to send to the scripts (as described above)</li></ul></li></ul>

<ul><li>openvpnstart puts a warning in the OpenVPN log (in the Details… window) if the path to the up or down script is very long, which could result in OpenVPN sending incomplete arguments to the scripts. (OpenVPN truncates the command line it uses to start the scripts to 255 characters.)"</li></ul>

<ul><li>Warnings from the openvpnstart program are now included in the OpenVPN log displayed in the 'Details…' window</li></ul>

<ul><li>Fixes bug that caused load of tap devices to fail when connecting</li></ul>

<ul><li>Fixes bug that sometimes caused log file contents not to display</li></ul>

<ul><li>Fixes bug that caused output from leasewatch ('Monitor connection' checkbox checked) to be stored in a /tmp file instead of displayed in the OpenVPN Log on the Details... window for Tunnelblick VPN Configurations (.tblk packages)</li></ul>

<ul><li>Fixes bug with 'connect on computer start' causing Tunnelblick to ask, in error, to flip the value of the checkbox</li></ul>

<ul><li>Fixes bug with 'when Tunnelblick launched' and 'when computer starts' radio buttons</li></ul>

<hr />

<b>3.1beta02 (2010-05-14)</b>
<ul><li>Polish (PL) localization by Grzegorz Danecki. Dziękuję bardzo!<br>
</li><li>Additional Norwegian (Bokmål, NB) localization by Jon Luberth. Tusen takk!<br>
</li><li>Additional French (FR) localisation by François Varas. Merci beaucoup!<br>
</li><li>Additional Catalan localization by Aleix Dorca. Moltes gràcies!</li></ul>

<ul><li>Many thanks also to Michael Williams. Many new enhancements are possible due to the his work. He contributed code that allows configurations in more than one folder to be available simultaneously. This has triggered an overhaul of the way Tunnelblick handles configurations, adding many new features.</li></ul>

<ul><li>Configurations may now be shared among all users of a computer, or they may be private to a particular user.<br>
<ul><li>A new button in the 'Details…' window makes changing the availability of a configuration easy. The button displays either 'Share configuration' or 'Make configuration private', as appropriate.<br>
</li><li>To be shared, a configuration must be a 'Tunnelblick VPN Configuration' (see below).<br>
</li><li>The Shared folder (/Library/Application Support/Tunnelblick/Shared) and its contents are protected. It is owned by root and may only be modified by administrators.<br>
</li><li>Shared configurations (like deployed configurations) may only be examined, not edited. (But you can make it private, edit it, and then share it).</li></ul></li></ul>

<ul><li>A new kind of configuration, a 'Tunnelblick VPN Configuration', may be used and may be shared among all users of a computer, or remain private to an individual user (see <a href='cConfigT.md'>Tunnelblick VPN Configurations</a> for details):<br>
<ul><li>A Tunnelblick VPN Configuration is an OS X folder with an extension of '.tblk'.<br>
</li><li>A Tunnelblick VPN Configuration includes one .ovpn configuration file, and many include key and certificate files and shell scripts. It can also include default settings for per-configuration preferences and version information to help manage enterprise distribution of configurations.<br>
</li><li>Tunnelblick VPN Configurations must be installed before they can be used. They can be installed by double-clicking them, or dragging and dropping them on a Tunnelblick icon in Finder (but not the Tunnelblick icon in the Status Bar near the Spotlight icon). They can also be automatically installed when installing Tunnelblick by including them in the disk image. The user is given the option of installing them as private or shared. All of this behavior can be controlled and/or inhibited by preferences, which can be 'forced' in a Deployed version of Tunnelblick.<br>
</li><li>Tunnelblick VPN Configurations and their contents are secured. Key and certificate files, for example, may not be read by the user. (The protection is not as robust as that for Deployed configurations, so that users may edit the configuration, but they are secure in the sense that a user is never allowed to use a configuration that has not been authorized by a computer administrator.)</li></ul></li></ul>

<ul><li>Tunnelblick can now start Tunnelblick VPN Connections (clients or servers) when the computer starts:<br>
<ul><li>A new option in the Details window is available for Shared and Deployed .tblk packages: to connect automatically 'when the computer starts'.<br>
</li><li>When Tunnelblick is launched, it attaches itself to any OpenVPN processes which were started because of that option and allows control (disconnect/connect) of them, and displays their logs.<br>
</li><li>When Tunnelblick quits, it closes only those connections which do not have 'when computer starts' selected. Thus OpenVPN instances started outside of Tunnelblick will continue, as will those started by Tunnelblick at any time that have 'when computer starts' selected at the time Tunnelblick quits.<br>
</li><li>If any unknown OpenVPN processes are running a few seconds after Tunnelblick is launched (i.e., after it has 'hooked up' to ones it started because of the 'when the computer starts' option), it pops up a window which gives the user the option to terminate them or ignore them. A checkbox in the window allows the user to 'Do not display this message again, always ignore'. There is a preference, 'hookupTimeout' that is the number of seconds to try, with a default of five seconds.<br>
</li><li>Note that these 'when the computer starts' configurations must not ask for usernames, passwords, or private keys. (There is no user to ask, and no Tunnelblick to pull them out of the Keychain and give to OpenVPN.)</li></ul></li></ul>

<ul><li>Tunnelblick now deals with the .tun and .tap kexts more flexibly:<br>
<ul><li>Loads and unloads them on demand: loaded at connect, unloaded at disconnect. An load is ignored if the kext is already loaded and an unload is ignored if the kext is in use.<br>
</li><li>Scans the configuration file to determine if 'tap' or 'tun' is being used, and loads only the appropriate kext at connect. (Tunnelblick uses whatever is specified in the first 'dev' option in the configuration file.)<br>
</li><li>New per-configuration preferences can be used to override the automatic detection of which kexts to load at connect: -loadTapKext, -loadTunKext, -doNotLoadTapKext, and -doNotLoadTunKext are all to be prefixed by the configuration name. (If both 'load…' and 'doNotLoad…' preferences exist for a specific configuration, the specified kext will not be loaded.)<br>
</li><li>When Tunnelblick launches, it unloads net.tunnelblick.tun and net.tunnelblick.tap so that the versions in use will always be loaded from the running version of Tunnelblick.app. The unload will not occur if the kexts are in use -- for example, by an instance of OpenVPN started when the computer started.<br>
</li><li>If foo.tap and foo.tun are loaded when Tunnelblick launches, it offers to unload them. (They are the old Tunnelblick kexts.) This simplifies the transition to the new net.tunnelblick.tun/tap for most users without a computer restart.</li></ul></li></ul>

<ul><li>Configurations are now listed in case-INsensitive alphabetic order and are no longer surrounded by single-quote marks on the drop-down menu.</li></ul>

<ul><li>You can now include private and/or shared configurations in Deployed configurations. This is NOT DONE UNLESS a preference named 'useLibraryConfigurationsWithDeployedOnes' and/or 'useSharedConfigurationsWithDeployedOnes' (boolean) is forced TRUE in the 'forced-preference.plist' file.</li></ul>

<ul><li>If a deployed configuration and/or a shared configuration and/or a normal configuration ( in ~/Library/Application Support/Tunnelblick/Configurations) have the same names, the deployed one will be displayed if it exists, otherwise the shared one will be displayed if it exists, and the other(s) will be hidden and unavailable. A warning will be issued to notify the user if any configurations are hidden.</li></ul>

<ul><li>Shared configurations are indicated by '(Shared)' after their names in the Tunnelblick menu and in the title of the "Details…" window, and private configurations are indicated by '(Private). If there are also deployed configurations, they are indicated by '(Deployed)' after their names.</li></ul>

<ul><li>The 'Edit Configuration' button becomes 'Examine Configuration' when the configuration may not be edited, i.e., it is a Deployed or Shared configurations.</li></ul>

<ul><li>Editing a configuration file requires it to be unprotected first, even on Snow Leopard.</li></ul>

<ul><li>After unprotecting a configuration file, the previous version (which is still protected) is available as xxx-previous. (If a non-administrator accidentally or mistakenly unprotects a configuration they will still be able to connect by using the xxx-previous version.)</li></ul>

<ul><li>The full path of the configuration file is displayed as a tooltip for connection names in the Tunnelblick menu.</li></ul>

<ul><li>Tunnelblick now detects it is located on a volume which doesn't support suid (thumb drives and network volumes, for example). In that circumstance, Tunnelblick offers to install itself to /Applications on the boot volume (the same way it does when Tunnelblick.app is located on a disk image).</li></ul>

<ul><li>Note that although Tunnelblick cannot run from such a volume, configurations can reside on such a volume, or even on a volume that does not support root ownership of files, such as a network volume or a volume formatted as FAT32. Configurations on such a volume will be 'shadow copied' to the boot volume before being used. This is done automatically for network volumes, and will be done for non-network volumes if the 'useShadowConfigurationFiles' preference is true.</li></ul>

<ul><li>Changed title of 'OpenVPN Log - Tunnelblick' window to 'Details - Tunnelblick'.</li></ul>

<ul><li>Removed extra Console Log message that the program needed repair.</li></ul>

<ul><li>Fix omission and improve formatting of openvpnstart command line tool.</li></ul>

<ul><li>Deals better with situation of ~/Library/openvpn and /Library/Application Support/Tunnelblick/Configurations being inconsistent.</li></ul>

<ul><li>Fixed bug that sometimes ignored the 'updateSendProfileInfo' preference.</li></ul>

<ul><li>Fixed bug that sometimes send partial anonymous profile information when checking for updates.</li></ul>

<ul><li>Fixed bug that caused wildcard matches of forced preferences to always fail.</li></ul>

<ul><li>Fixed bug that allowed setting of user preferences for forced preferences (although they are then ignored).</li></ul>

<ul><li>Fixed bug that caused incorrect permissions (644) to be set on subfolders of Tunnelblick.app/Contents/Resources/Deploy, making them inaccessible. If an existing deployed version of Tunnelblick has such subfolders, upon update (via the built-in updater or a fresh .dmg) the permissions of subfolders will be corrected (to be 755) at first launch).</li></ul>

<ul><li>Fixed bug that sometimes created and used shadow copies of Deployed configurations.</li></ul>

<ul><li>Fixed bug that caused unnecessary check of ownership/permissions of Tunnelblick.app/Contents/Resources/Deploy.</li></ul>

<hr />

<h2>Version 3.0</h2>

<hr />

<b>3.0.1 (2011-01-12)</b>

<ul><li>Fixes bug that causes a serious <a href='vulnerability20110112FAQ.md'>security vulnerability</a>.<br>
</li><li>Fixes bugs relating to forced-preferences.plist wildcards used in Deployed versions of Tunnelblick.<br>
</li><li>Added full Norwegian localization and added missing German localization of one string.</li></ul>

<hr />

<b>3.0 (2010-03-03)</b>
<ul><li>Fixes incorrect display of 'Automatically Check for Updates' preference on first run after some updates.<br>
</li><li>Out of beta!</li></ul>

<hr />

<b>3.0b28 (2010-02-24)</b>

<ul><li>Wildcards for forced preferences (see <a href='cDeployingTunnelblick.md'>Deploying Tunnelblick</a>).<br>
</li><li>Displays configuration name in title of "Details…" window.<br>
</li><li>Inserts full command line used for starting OpenVPN into the "Details…" window.<br>
</li><li>Full German localization. Many thanks to Markus Schneider.</li></ul>

<hr />

<b>3.0b26 (2010-02-09)</b>
<ul><li>Now uses OpenVPN version 2.1.1.<br>
</li><li>Adds Chinese localization (both simplified and traditional). Many thanks to Aming Lau.<br>
</li><li>Installation has been simplified: The Tunnelblick disk image gives instructions to "Double-click to begin" in several languages. Double-clicking starts a small installer. The installer detects installs/reinstalls/upgrades/downgrades and puts the current copy of Tunnelblick.app in the Trash before replacing it, then offers to launch the new version. Warns about other copies of Tunnelblick running during an install and offers to stop them. (Simply copying Tunnelblick.app to /Applications or elsewhere on the hard drive still works, too.)<br>
</li><li>The "Welcome to Tunnelblick" window now gives the user much more information, and offers the options of creating and editing a sample configuration file or opening the Configurations folder in Finder.<br>
</li><li>Uses Sparkle Updater version 1.5b6 for better security. Updates must be signed with 2048-bit DSA signatures. Updating behavior is now controlled by Tunnelblick preferences, which may be forced. Deployers note: many of these preferences should be forced for security reasons in a deployed environment.<br>
</li><li>Tunnelblick now explains why it is asking for an administrator username/password in authentication dialogs.<br>
</li><li>Tunnelblick's "Details…" window now includes detailed information about why a connection was restarted by leasewatch (when the 'Monitor connection' checkbox is checked).<br>
</li><li>The program's menu has been streamlined.<br>
</li><li>Connection timers are now displayed by default (unless the 'showConnectedDurations' preference is FALSE).<br>
</li><li>Fixes problem editing configuration files on Tiger and Leopard by allowing non-admin users (without an administrator username/password) to unprotect the configuration file before invoking <code>TextEdit</code>. This ability can be disabled with the 'onlyAdminsCanUnprotectConfigurationFiles' preference. On Snow Leopard (which automatically unprotects files when they are modified), warns user that an administrator username/password will be required to connect if the configuration file is modified. Note: The 'Edit Configuration' button may be still disabled with a per-configuration  preference.<br>
</li><li>Enhancements: Displays command line used to launch 'openvpnstart' in the "Details…" window. Detects and gives a detailed error message if a configuration file is identical to the sample provided by Tunnelblick. Creates a "Launch Tunnelblick" link in the Configurations folder. Localizes paths that are displayed to the user -- for example, in French (FR), 'Library' becomes 'Bibliothèque'. Detects, complains, and quits if not running on OS X 10.4 ("Tiger") or above. Added Quick Start Guide to disk image.<br>
</li><li>Bug fixes: Fixes bug that caused crashes when started automatically on login on some versions of Leopard and Snow Leopard. Fixes bug that didn't localize the title for the "Details…" window. Fixes bug that displayed 'monitoring connection' when 'Set nameserver' is not checked. Fixes bug opening wrong copy of sample configuration file in <code>TextEdit</code>. Fixes bug that tries to to create Configurations folder when not necessary. Fixes bug that tried to create configuration file in Deploy. Fixes typo in dialog for remote home folders. Fixes sporadic failure to detect multiple simultaneous connections.<br>
</li><li>Known Issues: See the <a href='cKnown.md'>Known Issues wiki</a>.</li></ul>

<hr />

<b>3.0b24 (2009-12-12)</b>
<ul><li>New 'Monitor connection' checkbox in the "Details…" window (defaults to checked). When checked, Tunnelblick monitors connection interfaces as it has since 3.0b18. When unchecked, Tunnelblick ignores connection interface changes, as version 3.0b10 did. This allows more users to use the latest version (some users couldn't because of repeated restarts caused by Tunnelblick detecting connection interface changes). Please note that OpenVPN itself restarts connections under certain circumstances. New scripts are used when 'Monitor connection' is not checked and 'Set DNS' is checked: client.nomonitor.up.osx.sh and client.nomonitor.down.osx.sh.<br>
</li><li>New 'Options' submenu has entries to change commonly used preferences, check for updates, and view the 'About…' window.<br>
</li><li>Tun/tap kernel extensions are loaded when Tunnelblick launches and unloaded when Tunnelblick quits.<br>
</li><li>Configuration and other files are now located in ~/Library/Application Support/Tunnelblick/Configurations to conform to OS X standards. The ~/Library/openvpn folder is moved to this new location automatically during the first launch of Tunnelblick after updating to 3.0b24, and is replaced by a symbolic link to the new location. For details see <a href='http://groups.google.com/group/tunnelblick-discuss/t/d8f000d1e854b39d'>http://groups.google.com/group/tunnelblick-discuss/t/d8f000d1e854b39d</a>.<br>
</li><li>Adds Català (Catalan) localization, thanks to Aleix Dorca.<br>
</li><li>Additional Español (Spanish) and Deutsch (German) localization, thanks to Diego Rivera and Markus Schneider, respectively.<br>
</li><li>Adds OS X version information to the start of the OpenVPN Log.<br>
</li><li>Adds configuration, 'Set nameserver', and 'Monitor connection' status to the OpenVPN Log before attempting to make a connection.<br>
</li><li>Adds new Deployment features:<br>
<ul><li>Always restores the Resources/Deploy folder from a backup if it does not exist and a backup does. An entry is put in the Console Log, but no other user notification is made. (This happens after an auto-update without the Deploy folder.)<br>
</li><li>Monitors Resources/Deploy (if it exists) for changes to configuration files.<br>
</li><li>If Deploy contains only <code>*</code>.conf, <code>*</code>.oven, <code>*</code>.up.sh, <code>*</code>.down.sh, and forced-preferences.plist files, then the ~/Library/openvpn folder will be used for all other files (including other scripts).<br>
</li><li>If 'Set nameserver' is checked and 'Monitor connection' is checked, then if Deploy/<i>CONFIGNAME</i>.up.sh exists, it will be used instead of Resources/client.up.osx.sh, and if Deploy/<i>CONFIGNAME</i>.down.sh exists, it will be used instead of Resources/client.down.osx.sh.<br>
</li><li>If 'Set nameserver' is checked and 'Monitor connection' is <i>not</i> checked, then if Deploy/<i>CONFIGNAME</i>.nomonitor.up.sh exists, it will be used instead of Resources/client.nomonitor.up.osx.sh, and if Deploy/<i>CONFIGNAME</i>.nomonitor.down.sh exists, it will be used instead of Resources/client.nomonitor.down.osx.sh.<br>
</li><li>If 'Set nameserver' is checked, then if the '<i>CONFIGNAME</i>-useDownRootPlugin' preference is true, then Resources/openvpn-down-root.so will be used as a plugin for OpenVPN.<br>
</li><li>Sets owner to root:wheel and permissions to 600 for .cer, .crt, .der, .key, .p12, .p7b, .p7c, .pem, and .pfx files in the Deploy folder.<br>
</li></ul></li><li>Adds new per-configuration preferences:<br>
<ul><li>'CONFIGNAMEdisableEditConfiguration' is a boolean. If set, disables the 'Edit configuration' button. If cleared (the default), enables the button.<br>
</li><li>'<i>CONFIGNAME</i>-notMonitoringConnection' is a boolean. If present, its value reflects/is used for the 'Monitor connection' checkbox. Default is set.<br>
</li><li>'<i>CONFIGNAME</i>-useDownRootPlugin' is a boolean. If set, causes the 'openvpn-down-root.so' plugin to be loaded. If cleared (the default), the plugin is not loaded.<br>
</li></ul></li><li>Closing a connection, putting the computer to sleep, or quitting Tunnelblick may be delayed a few seconds while Tunnelblick waits for OpenVPN processes to terminate.<br>
</li><li>Bug fixes: Fixes bug that sometimes caused authentication failures with usernames or passwords longer than 12 characters. Fixes bug that sometimes caused the 'Retry' button to be interpreted as 'Cancel' in the Authentication Failed dialog. Fixes bug that caused a connection attempt to fail with a 'script failed: could not execute external program' error if 'Set nameserver' is checked and there is a space character in the name of Tunnelblick.app or in the path to it. Fixes bug that caused 'Get Info' of Tunnelblick.app to show incorrect copyright information. Fixes bug that often caused loss of last few lines of OpenVPN Log before disconnecting. Fixes bug that sometimes caused problems restoring connections when awakening from sleep. Fixes bug that sometimes caused the Sparkle updater window to not appear on Snow Leopard. Fixes inconsistent logging of ownership/permissions repairs. Fixes bug that caused Tunnelblick to check for updates at launch even though preference to do so was cleared, not set. Fixes bug that ignored forced-preferences.plist when there was no configuration files in Deploy. Fixes bug with configuration files that are actually symbolic links. Fixes bug that didn't verify that ownership/permissions on Deploy contents copied correctly to backup. Complains with specific message in Console log if a configuration file needs repair but is locked. Fixes problems when a configuration file is a link.</li></ul>

Known Issues:<br>
<ul><li>The standard scripts that "Set nameserver" uses handle DNS for most common setups. You must use custom scripts to do anything else. See <a href='UsingTunnelblick.md'>Using Tunnelblick</a> for details.<br>
</li><li>Localization is not complete.</li></ul>

<hr />

<b>3.0b22 (2009-11-01)</b>
<ul><li>Includes OpenVPN version 2.1_rc20, which fixes problems with the "redirect-gateway" option.<br>
</li><li>Includes the 32/64-bit version of tuntap, which fixes problems running Tunnelblick on Snow Leopard under the 64-bit kernel. Thanks to the tuntap project, to Mohammad A. Haque for Xcode help, and to Jean-Philippe Jung for testing.<br>
</li><li>Stores username in Keychain instead of preferences.<br>
</li><li>Stores shadow copies of configuration files in /Library/Application Support/Tunnelblick/Users/<i>username</i> instead of /Library/Tunnelblick/<i>username</i>.<br>
</li><li>Bug fixes: Fixes bugs that interfere with storage or retrieval of usernames and passwords. Adds new configs to "Details…" window when it has been opened but is currently closed. Clears "automatically launch Tunnelblick upon login" for error exits. Clean exit if 'running from .dmg' error. Fixes several memory and CF leaks. Fixes bug that caused attempt to kill openvpn process that had already been killed. Fixes potential problem detecting locked configuration files during shadow copying. Installer detects and reports errors making ownership and permission modifications.<br>
</li><li>Enhancement: Creates openvpn-down-root.so and puts a copy of it in Tunnelblick.app/Contents/Resources, allowing use of OpenVPN 'user' and 'group' options by adding a line to the configuration file. See<a href='UsingTunnelblick.md'>Using Tunnelblick</a> for details.<br>
</li><li>Deployment enhancements: Several changes have been made which make it easy to create a customized version of Tunnelblick that can easily be deployed to multiple clients or installed once for all users of a computer. Configuration, key, and certificate files and up/down scripts can be put into a Deploy folder within Tunnelblick.app, and Tunnelblick will use them instead of using files in ~/Library/openvpn. These files are read-only, and, combined with read-only preference overrides, can create a tamper-proof application. Such deployed applications may be updated via the automatic update mechanism without losing the configuration information. Detailed information is available in <a href='cDeployingTunnelblick.md'>Deploying Tunnelblick</a>.<br>
</li><li>Other enhancements: Clarifies language in a few places. Adds a specific error message if unrecoverable error. Warns if all config files removed and gives a choice of quitting or installing and editing a sample config file. Warns if zero-length passphrase, username, or password. Adds Tunnelblick icon and the configuration name to all applicable dialog windows. Puts dialogs on top of other windows.</li></ul>

Known Issues:<br>
<ul><li>The standard scripts that "Set nameserver" uses handle DNS for most common setups. You must use custom scripts to do anything else. See <a href='UsingTunnelblick.md'>Using Tunnelblick</a> for details.<br>
</li><li>Localization is not complete.</li></ul>

<hr />

<b>3.0b20 (2009-10-09)</b>
<ul><li>Fixes issues with "Set nameserver" on Snow Leopard.<br>
</li><li>Inhibits console message that tun and tap are already loaded.<br>
</li><li>Sends details of some error messages to the "Details…" window instead of the Console log.<br>
</li><li>Prefixes all non-OpenVPN messages in the log window with "<code>*</code>Tunnelblick:".</li></ul>

Known Issues:<br>
<ul><li>Does not work under Snow Leopard when booted into 64-bit mode. (Works when booted into 32-bit mode.)<br>
</li><li>The "--redirect-gateway" OpenVPN option fails silently, causing incorrect routing, if no flags are specified (which is a syntax error). Previously, a flag of "def1" was assumed.<br>
</li><li>Localization is not complete.<br>
</li><li>The standard scripts that "Set nameserver" uses handle DNS for most common setups. You must use custom scripts to do anything else. See <a href='UsingTunnelblick.md'>Using Tunnelblick</a> for details.</li></ul>

<hr />

<b>3.0b18 (2009-09-23)</b>
<ul><li>Implements different behavior when configuration files change: when a configuration file is added, all connections are maintained. When a configuration file is deleted, only the corresponding connection is disconnected (and an alert window is displayed). In either case, the menu and Log window reflect the change immediately without restarting Tunnelblick. Changes to a configuration file's contents or metadata are ignored (but will be used the next time a connection is attempted).<br>
</li><li>Works with home folders on network volumes and/or when the home folder is not permitted to have files owned by root. This is implemented transparently with "shadow" copies of configuration files. It is automatic if the config file is on a network volume or if Tunnelblick's "useShadowConfigurationFiles" preference is set.<br>
</li><li>Moves "Set nameserver" checkbox to avoid inadvertent changes.<br>
</li><li>Fixes issues when DNS is set manually, when 'dhcp-option DOMAIN ...' is pushed to the client, and when --remote-random is used under certain circumstances.<br>
</li><li>Fixes misleading language in window that requests a username/password for the VPN.<br>
</li><li>Fixes a bug which caused "Details…" window to stay on top of all other windows if it was opened within 3 seconds of starting Tunnelblick.<br>
</li><li>Fixes a bug which caused config file changes to be ignored under certain circumstances.<br>
</li><li>Fixes a bug which interferes with saving a username/password combination or a passphrase to the Keychain when there is more than one simultaneous connection.<br>
</li><li>Fixes a bug which causes a (quitable) infinite loop if an error occurred while changing ownerships and/or permissions.<br>
</li><li>Fixes a bug which sometimes causes non-English text of buttons or checkboxes to be truncated or clipped.<br>
</li><li>Makes changes to ownership and permissions of parts of Tunnelblick.app for better security.<br>
</li><li>Adds support for WINS configurations from the server when using the standard up/down scripts (i.e., when the "Set nameserver" checkbox is checked).<br>
</li><li>Warns about multiple simultaneous connections, with a checkbox to suppress such warnings.<br>
</li><li>Displays duration times only for connected tunnels.<br>
</li><li>Updated to UKKQueue 0.5 and LZO 2.03<br>
</li><li>Adds Spanish localization (thanks to Diego Rivera).</li></ul>

Known Issues:<br>
<ul><li>Does not work under Snow Leopard when booted into 64-bit mode. (Works when booted into 32-bit mode.)<br>
</li><li>The "--redirect-gateway" OpenVPN option fails silently, causing incorrect routing, if no flags are specified (which is a syntax error). Previously, a flag of "def1" was assumed.<br>
</li><li>Localization is not complete for French, German, Japanese, Korean, Norwegian, or Spanish.<br>
</li><li>The standard scripts that "Set nameserver" uses handle DNS for most common setups. You must use custom scripts to do anything else. See <a href='UsingTunnelblick.md'>Using Tunnelblick</a> for details.</li></ul>

<hr />

<b>3.0b16 (2009-08-22)</b>

<ul><li>Upgraded to OpenVPN version 2.1_rc19<br>
</li><li>Additional French translations (contributed by Oliver Hill)<br>
</li><li>An entry is appended to the "Details…" window if OpenVPN returns with an error code. (This typically happens when there is an error in the configuration file.)</li></ul>

Known Issues:<br>
<ul><li>Home folders cannot reside on remote volumes (AFS, NFS, etc.)<br>
</li><li>Japanese and Norwegian localization is not complete.<br>
</li><li>The standard scripts that "Set nameserver" uses handle DNS for the most common DHCP setups. You must use custom scripts to do anything else. The standard scripts:<br>
<ul><li>Do not support multiple simultaneous connections<br>
</li><li>Do not support multiple nameservers for multiple domains (e.g., local nameserver and remote nameserver simultaneously)<br>
</li><li>Do not remove manual DNS entries (i.e., the manual nameserver will continue to be used even when the tunnel is open even if the OpenVPN "redirect-gateway" option is specified)</li></ul></li></ul>

<hr />

<b>3.0b14 (2009-08-10)</b>

<ul><li>Fixed issues where DNS settings were not saved properly, and when DHCP is renewed (contributed by Diego Rivera)<br>
</li><li>Added support for PKCS#11 and Security Tokens, e.g. Aladdin eToken (contributed by Xaver Loppenstedt)<br>
</li><li>Additional Korean and German translations (contributed by Markus Schneider and Kyoungmin Kim)<br>
</li><li>Animation improvements, including the ability to have "icon sets" (contributed by Raal Goff). Note: the user interface for this feature is not included yet<br>
</li><li>Fixed issue with "Set nameserver" and "Auto connect on launch" checkboxes being cleared on quit if the "Details…" window was never displayed<br>
</li><li>Fixed issue which caused disconnects when any file in ~/Library/openvpn was accessed (for example, by backup software). (Note that changing, adding, or deleting any configuration files will close all open connections)<br>
</li><li>Fixed issue with failed authentication: now handled gracefully: allows cancel or retry. If credentials are stored in the Keychain, also allows retry with new credentials (by deleting the old credentials before the retry)<br>
</li><li>Fixed issue with multiple connections with same username; separate passwords are now kept for each username<br>
</li><li>Fixed issue in dialog about configuration files - the correct path is now shown: "~/Library" instead of "/Library"<br>
</li><li>Command-C, Command-X, Command-V (copy, cut, paste) and Command-A, Command-M, Command-W, and Command-Q (select all, minimize to the Dock, close window, and quit Tunnelblick) now work properly from the "Details…" window<br>
</li><li>Fixed issue which caused invalid dates/times to appear in the OpenVPN Log<br>
</li><li>Shows connection duration in "Details…" window's tabs<br>
</li><li>Fixed issue which caused the "Details…" window to remain underneath other windows when the "Details..." menu item is clicked<br>
</li><li>Added date/time and Tunnelblick and OpenVPN version info at the beginning of the OpenVPN Log and whenever it is cleared<br>
</li><li>Saves and restores "Details…" window size and position<br>
</li><li>Internationalized date/time displayed in the OpenVPN Log, including seconds<br>
</li><li>Fixed bug which caused Japanese localization to fail<br>
</li><li>Displays tab for the left-most established connection when the "Details…" window is first displayed. If no established connection exists, displays the left-most tab<br>
</li><li>Added the "Using Tunnelblick.html" document to the installation disk image<br>
</li><li>Added preference, "doNotMonitorConfigurationFolder" (default = False) to disable monitoring of the configuration folder for changes to the configuration files<br>
</li><li>Added preference, "placeIconInStandardPositionInStatusBar" (default = False) to have the Tunnelblick icon placed normally in the Status Bar -- to the left of other items (contributed by Raal Goff and Michael Schloh von Bennewitz)<br>
</li><li>Added an "About" window that displays a link to the website, Tunnelblick version and build numbers, and the OpenVPN version number, which is dynamically extracted from the openvpn program (and thus always reports the version of OpenVPN which is actually being used).<br>
</li><li>Fixed issue which caused Tunnelblick to pass the "script-security 2" arguments to OpenVPN even if a version of OpenVPN which doesn't support that argument is being used<br>
</li><li>openvpnstart enhancements:<br>
<ul><li>The "Set nameserver" argument is now optional and defaults to 0 (NO)<br>
</li><li>Optional argument skips passing the "script-security 2" arguments to OpenVPN.<br>
</li><li>Improved error checking and reporting<br>
</li><li>Displays usage instructions if invoked with no arguments<br>
</li><li>Fixed program crashes caused by improper syntax<br>
</li><li>"killall" command shows # of openvpn processes killed if non-zero</li></ul></li></ul>

Known Issues:<br>
<ul><li>Home folders cannot reside on remote volumes (AFS, NFS, etc.)<br>
</li><li>French, Japanese, and Norwegian localization is not complete.<br>
</li><li>The standard scripts that "Set nameserver" uses handle DNS for the most common DHCP setups. You must use custom scripts to do anything else. The standard scripts:<br>
<ul><li>Do not support multiple simultaneous connections<br>
</li><li>Do not support multiple nameservers for multiple domains (e.g., local nameserver and remote nameserver simultaneously)<br>
</li><li>Do not remove manual DNS entries (i.e., the manual nameserver will continue to be used even when the tunnel is open even if the OpenVPN "redirect-gateway" option is specified)</li></ul></li></ul>

<hr />

<b>3.0b10 (2008-11-20)</b>

<ul><li>fix linking problem that resulted in lzo compression not working on PowerPC<br>
</li><li>prevent user from launching tunnelblick directly from the dmg<br>
</li><li>remove experimental status from 'Set Nameserver' and make it the default<br>
</li><li>upgrade to OpenVPN 2.1_rc15<br>
</li><li>let buffered openvpn log messages appear in the GUI log<br>
</li><li>possible fix for the crash if password is mistyped when using username/password authentication<br>
</li><li>add version number to plist file<br>
</li><li>don't restart connections on NetworkDidChange notification. fixes issue where existing connections would be reset when starting multiple simultaneous vpn connections.<br>
</li><li>always use --script-security 2 so users are allowed to supply custom up/down scripts. needed for OpenVPN 2.1<br>
</li><li>add missing example config file<br>
</li><li>properly escape special chars in username or password/passphrase before passing them over to the management interface. fixes issue where the password/passphrase was not accepted when it contained backslashes or " chars.<br>
</li><li>use NSStatusWindowLevel for notification windows. fixes issue that Tunnelblick icon remained visible in spaces or fullscreen mode of some apps.<br>
</li><li>increase robustness when killing openvpn children by explicitly sending the SIGTERM to the process id instead of just sending "signal SIGTERM" over the management socket<br>
</li><li>kill all openvpn processes on quit. fixes a rare condition where openvpn processes would be left over on Tunnelblick  quit<br>
</li><li>Add German, French, Japanese, Korean and Norwegian translations</li></ul>

<hr />

<b>3.0b9 (2008-07-24)</b>

<ul><li>Fixed the crash on Leopard<br>
</li><li>Fixes the slow shutdown issue<br>
</li><li>Updated to the new tun/tap drivers<br>
</li><li>Auto-Update Capability using Sparkle</li></ul>

<hr />

<h3>PLEASE USE THE <a href='http://groups.google.com/group/tunnelblick-discuss'>TUNNELBLICK DISCUSSION GROUP</a> FOR COMMENTS OR QUESTIONS</h3>