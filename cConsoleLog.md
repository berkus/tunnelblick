**NOTES:
  1. Tunnelblick 3.3beta38 and higher include the "tail" of the Console log in the data copied to the Clipboard by the 'Copy Diagnostic Info to the Clipboard' button on the 'Settings' tab of the 'Configurations' panel of the 'VPN Details…' window.
  1. Tunnelblick 3.3beta48 and higher include a "Copy Console Log to Clipboard" button, which copies relevant (Tunnelblick and OpenVPN) Console Log entries to the Clipboard.**

Tunnelblick and OpenVPN sometimes output diagnostic information to the OS X logs. The logs include output from all of the programs running on your computer, not just Tunnelblick and OpenVPN.

Tunnelblick's output to the Console log includes descriptions of installation activity, such as the ownership/permission changes that Tunnelblick makes when it is installed, and detailed information about some error conditions that Tunnelblick encounters. OpenVPN outputs detailed information about how a connection is established, maintained, and disconnected.

To view the Console log, launch the Console application, located at /Applications/Utilities/Console.app. The Console application is built into all versions of OS X.

If you don't see a list of different logs to view on the left of the Console window, click "View", then "Show Log List".

If you don't see a toolbar at the top of the Console window, click "View", then "Show Toolbar".

All of Tunnelblick's messages appear in the Console log, which you can view by selecting "Console Messages" in the log list on the left of the Console window. OpenVPN may output messages which only appear when viewing "All Messages" in the log list.

There is a "Filter" text box in the upper right corner of the Console window. If you type "tunnelblick" (without the quote marks) into the text box, Console will only show messages from Tunnelblick, not from other programs.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS