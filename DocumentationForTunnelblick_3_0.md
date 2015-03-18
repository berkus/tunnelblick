<font color='red'>Note: Tunnelblick 3.0 is not the latest stable version of Tunnelblick. See the <a href='DownloadsEntry.md'>Downloads page</a> for the latest stable version of Tunnelblick.</font>

This is a summary of major changes from Tunnelblick version 3.0b10 to version 3.0. For more details or changes from other versions to Tunnelblick 3.0, see the [Tunnelblick Release Notes](RlsNotes.md).

## Better Security ##
  * Includes the latest stable version of OpenVPN.
  * Requires DSA signatures on updates.
  * Stores usernames in the Keychain instead of preferences.
  * "openvpn-down-root" support allows OpenVPN to run as an unprivileged user.

## Better Usability ##
  * New 'Options' submenu has entries to change commonly used preferences, check for updates, and view the 'About...' window.
  * Guided installation process.
  * Administrators can now edit protected configuration files.
  * Standard keyboard shortcuts work in the Details... window.
  * Maintains all connections when new configurations are added.
  * Failed authentication is now handled gracefully.

## More Capabilities ##
  * Works with home folders on network volumes or if the home folder is not permitted to have files owned by root.
  * Adds support for WINS configurations pushed from the server.
  * Restarts the connection if necessary to reflect changes in the network configuration.
  * Adds support for multiple authenticated connections with the same username.
  * New features allow easy creation of customized versions of Tunnelblick for simple deployment to multiple users.

## Better Reliability ##
  * Fixes problems that caused "Set nameserver" and "Auto connect on launch" checkboxes to be cleared on quit if the "Details..." window was never displayed.
  * Fixed problems that caused disconnects when any file in ~/Library/openvpn was accessed (for example, by backup software).
  * Fixes problems that interfered with storage or retrieval of usernames and passwords.
  * Fixed problems that interfered with saving DNS settings (contributed by Diego Rivera).
  * Fixed problems that caused problems with DNS settings upon DHCP renewal (contributed by Diego Rivera).
  * Fixes problems that caused crashes when running under the 64-bit Snow Leopard kernel.

## Better Localization ##
  * Complete German translation -- many thanks to Markus Schneider.
  * Partial translations for Catalan, Chinese (both simplified and traditional), Spanish, French, and Korean. Thanks to Aleix Dorca, Aming Lau, Diego Rivera, Oliver Hill, and Kyoungmin Kim, respectively.

### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###