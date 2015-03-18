## Summary of Changes from Version 3.3 to Version 3.4 ##

> For details of the changes from Tunnelblick version 3.3 to version 3.4, see the [Release Notes](RlsNotes.md).

## Better Security ##
  * Fixes several security-related bugs.
  * Includes the latest stable versions of OpenVPN, LZO, the OpenSSL library, and Tuntap.
  * Uses https: for updates and IP address checks (still uses digital signatures for additional security).
  * Does additional checks to ensure the program's integrity.

## Better Usability ##
  * Enhances installation of configurations with improved error detection and correction and automatic conversion of OpenVPN configurations.
  * On OS X 10.6 ('Snow Leopard') and higher, allows the user to select multiple configurations in the VPN Details… window and then change settings for all of the selected configurations.
  * Includes a new status icon (the icon in the menu bar) more in keeping with recent OS X aesthetics.
  * Changes many warning dialogs so they do not block other Tunnelblick operations.

## More Capabilities ##
  * On OS X 10.6.8 and higher when using OpenVPN 2.3.3 and higher in a TUN configuration, Tunnelblick no longer automatically loads the tunnelblick tun kernel extension (kext). In this situation, OpenVPN will use the UTUN device driver built into OS X.
  * Runs on OS X 10.4 through 10.10 ("Tiger", "Leopard", "Snow Leopard", "Lion", "Mountain Lion", "Mavericks", and "Yosemite").

## Better Reliability ##
  * Fixes many (most? all?) problems. Please report problems to the [Tunnelblick Discussion Group](https://groups.google.com/forum/#!forum/tunnelblick-discuss).

## Worse Localization ##
  * Sorry, but 3.4.0 does not have complete localization.
  * To help with localization, please email jkbullard at gmail for instructions.



&lt;hr&gt;


<table><tr><td align='center'>
<blockquote><a href='https://code.google.com/p/tunnelblick/wiki/DownloadsEntry#Tunnelblick_Stable_Release'>
<blockquote><img src='http://tunnelblick.googlecode.com/files/green-arrow-120x120.png' /><br />Download<br>
</blockquote></a>
</td></tr></table></blockquote>



---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS