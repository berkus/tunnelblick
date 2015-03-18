

&lt;hr&gt;


<font size='3'><b><a href='http://code.google.com/p/tunnelblick/wiki/DownloadsEntry?tm=2'>Download Tunnelblick</a></b></font>


&lt;hr&gt;



This is a summary of major changes from Tunnelblick version 3.1 to version 3.2.
  * For more details of the changes from Tunnelblick version 3.1 to version 3.2, see [Details About 3.2](cThreeOneToThreeTwoChanges.md).
  * For changes from other versions to Tunnelblick 3.2, see the [Tunnelblick Release Notes](RlsNotes.md).

## Better Security ##
  * Includes the latest stable versions of OpenVPN (2.2.1), PKCS#11 (1.09), LZO (2.05), the OpenSSL library (1.0.e), and Tuntap (20111101).
  * Includes additional protection against attacks.

## Better Usability ##
  * The Tunnelblick menu has been streamlined.
  * The new "VPN Details…" window lets you easily:
    * Manage configurations -- you can easily add, delete, duplicate, and rename configurations, remove Keychain credentials, etc.
    * Change configuration settings
    * Change Tunnelblick's behavior and appearance.
  * Tunnelblick now allows copy/cut/paste of VPN usernames and paste of passwords and passphrases.
  * Tunnelblick is now less sensitive to minor network changes.
  * Tunnelblick includes complete localization in 17 languages: Catalan, Czech, German, English, Spanish, French, Hungarian, Japanese, Italian, Korean, Norwegian, Dutch, Polish, Portuguese, Russian, Swedish, and Chinese (simplified).
  * The Tunnelblick application is now digitally signed, so that the user will not be asked to authorize Tunnelblick to use the Keychain each time the program is updated (on OS X 10.5 "Leopard" and above).

## More Capabilities ##
  * Runs on OS X 10.4, 10.5, 10.6, and 10.7 ("Tiger", "Leopard", "Snow Leopard", and "Lion").
  * [AppleScript support](cAppleScriptSupport.md).
  * Scripts may be automatically run before and tun/tap kexts are loaded, after a connection has been made, when a reconnection attempt is being made, and after a connection has been disconnected. For more details, see [Using Scripts](cUsingScripts.md).
  * Includes OpenVPN 2.1.4 and OpenVPN 2.2.1; the user can choose which version to use.
  * The status message (the first line of the menu exposed when you click the Tunnelblick icon) allows you to disconnect all open connections with one click.
  * Higher 'verb' levels may be used without performance degradation.

## Better Reliability ##
  * Fixes several bugs, including:
    * Fixes problems with Fast User Switching.
    * Fixes problems using TAP, DHCP, and 'Set nameserver (alternate 1)'.
    * Fixes failure to to alert the user when a VPN username/password or passphrase fails. Offers to try using different credentials.
    * And many more… (See the [Release Notes](RlsNotes.md) for details.



&lt;hr&gt;


<font size='3'><b><a href='http://code.google.com/p/tunnelblick/wiki/DownloadsEntry?tm=2'>Download Tunnelblick</a></b></font>


&lt;hr&gt;




---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS