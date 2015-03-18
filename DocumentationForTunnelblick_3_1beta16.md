

&lt;hr&gt;


<font size='3'><b><a href='http://code.google.com/p/tunnelblick/downloads/detail?name=Tunnelblick_3.1beta16.dmg'>Download Tunnelblick 3.1beta16</a></b></font>


&lt;hr&gt;



**[Full Release Notes](RlsNotes.md)**

## What's New in Tunnelblick 3.1beta16 (Changes from 3.1beta14) ##
  * <font color='red'><b>IMPORTANT NOTE FOR THOSE USING "WHEN COMPUTER STARTS" WITH EARLIER BETA VERSIONS:</b></font> The first time that you update to Tunnelblick 3.1beta08 or above from 3.1beta02 - 3.1beta06, Tunnelblick will not recognize any **running** "when computer starts" configurations. Five to ten seconds after you start Tunnelblick, they will be identified as unknown OpenVPN processes and you will be given the choice to leave them alone or disconnect them. You should chose to disconnect them in this dialog and then manually connect them in Tunnelblick. (You do not need to do this immediately, but you will not be able to control them with Tunnelblick. The dialog will appear each time you start Tunnelblick if these connections are still active.) This need only be done once, and is not necessary if there are no "when computer starts" configurations that are connected at the time you update.



  * Replaces the 'Set nameserver' checkbox with a drop-down list that can display additional choices to allow different up/down scripts to be used.
    * The following choices will always be displayed:
      * 'Do not set nameserver' to not use any scripts                  (equivalent to not having a check in the old 'Set nameserver' checkbox')
      * 'Set nameserver'        to use the standard Tunnelblick scripts (equivalent to having a check in the old 'Set nameserver' checkbox')
    * The following two additional choices will be displayed only if custom scripts are not being used:
      * 'Set nameserver (3.0b10)'      to use scripts from Tunnelblick 3.0b10 (for backward compatibility)
      * 'Set nameserver (alternate 1)' to use scripts based on Ben Low's scripts from http://openvpn.net/archive/openvpn-users/2006-10/msg00120.html. These scripts:
        * Implement multiple domains 'pushed' from the server
        * Fix some issues with some TAP connections that cause 'write to TUN/TAP : Input/output error (code=5)' and other errors
        * Do not implement 'Monitor connection'
    * Note: Some Deployed versions of Tunnelblick and Tunnelblick VPN configurations may include custom scripts that will inhibit the display of these two additional choices.
    * Running this version changes the 'useDNS' per-configuration preference from a boolean to a number. This is a downward-compatible change -- earlier versions of Tunnelblick may be run after running this version and modifying the 'Set nameserver' selection. The earlier version will consider anything other than 'Do not set nameserver' as if the 'Set nameserver' checkbox were checked.
    * Warning: If Build 2054 changes the setting to 'Set nameserver (3.0b10)' or 'Set nameserver (alternate 1)', using an earlier version of Tunnelblick to modify the checkbox so it is checked will revert the setting back to 'Set nameserver'.

  * Adds the ability to add menu items to the Tunnelblick menu to execute programs (e.g., scripts).
  * Adds the ability to specify programs that should be executed when Tunnelblick is launched or when a connection is attempted.
> (See [Additional Menu Commands and Programs](cCusDeployed#Additional_Menu_Commands_and_Programs.md) for details.)

  * Includes localization-related code tweaks by Stefan Bethke and additional German localization by Stefan Bethke, Marcus Schneider, and 'Dr Hok'.

  * Fixes a formatting error when displaying file permissions in error messages about being unable to change permissions.

  * Fixes a problem causing a connection restart when 'Set nameserver' is used, a DHCP renewal occurs, and there are no WINS settings.

  * Fixes issues when using OpenDirectory and the user's home directory is on a non-Mac platform.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS