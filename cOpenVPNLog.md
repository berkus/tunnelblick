The Tunnelblick log is the record of output from OpenVPN for a connection. It includes entries from Tunnelblick giving additional information.

<font color='red'><strong>If you want help troubleshooting connection problems, please set the "verb" level in your configuration file to "3" before making a connection attempt.</strong></font>

> You can set the "verb" level to "3" by adding the following line in your configuration file:

> verb 3

> If there is already such a line with a different number, just change the number. If there is already a line with a "3", leave it alone.

> The level of detail about OpenVPN operations in the log is controlled by OpenVPN's "verb" option. The default (if no "verb" option appears in the configuration file) is "verb 3". That usually provides sufficient information for finding problems, and does not log anything about ordinary traffic through the VPN, so it is the best choice. "verb" levels higher than 3 are usually not necessary, and "verb" levels 1 and 2 do not usually provide sufficient information to determine why a connection fails.

**NOTE: Tunnelblick 3.3beta38 and higher will include the Tunnelblick log in the data copied to the Clipboard by the 'Copy Diagnostic Info to the Clipboard' button on the 'Settings' tab of the 'Configurations' panel of the 'VPN Details…' window.**


You can view the Tunnelblick log for a configuration as follows:

  * Tunnelblick 3.2 and up:
    1. Click on the Tunnelblick icon at the top of the screen;
    1. Click "VPN Details…";
    1. Select the "Configurations" pane at the top;
    1. Select the configuration in the list on the left;
    1. To copy the log to the Clipboard, click the "Copy Log to Clipboard" button.

  * Earlier versions of Tunnelblick:
    1. Click on the Tunnelblick icon at the top of the screen;
    1. Click "Details…";
    1. Select the "Configurations" pane at the top;
    1. Select the configuration in the list on the left or select the tab for the configuration;
    1. To copy the log to the Clipboard, type Command-A, then Command-C.

**Tunnelblick adds information to the log**:
  * When started or when the log is cleared, Tunnelblick adds a line listing the versions of OS X, Tunnelblick, and OpenVPN.

  * When a connection attempt is made, Tunnelblick adds details to the log about what Tunnelblick does (as opposed to what OpenVPN does).

  * When OpenVPN notifies Tunnelblick that the connection is being terminated or restarted.

  * When the computer's system configuration changes.

Sometimes entries in the log (which are prefixed by the date and time) appear out of sequence. This is because the different programs writing to the log (Tunnelblick, OpenVPN, and scripts) buffer their output. In general, though, the dates and times listed are correct.

**You may use the standard keyboard shortcuts**:
|Command-C|Copy|
|:--------|:---|
|Command-X|Cut|
|Command-V|Paste|
|Command-A|Select all the text in the log|
|Command-M|Minimize the window to the dock|
|Command-W|Close the window|
|Command-Q|Quit Tunnelblick|



---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS