

&lt;hr&gt;


<font size='3'><b><a href='http://code.google.com/p/tunnelblick/downloads/detail?name=Tunnelblick_3.1beta24.dmg'>Download Tunnelblick 3.1beta24</a></b></font>


&lt;hr&gt;



**[Full Release Notes](RlsNotes.md)**

## What's New in Tunnelblick 3.1beta24 (Changes from 3.1beta22) ##
  * <font color='red'><b>IMPORTANT NOTE FOR THOSE USING "WHEN COMPUTER STARTS" WITH EARLIER BETA VERSIONS:</b></font> The first time that you update to Tunnelblick 3.1beta08 or above from 3.1beta02 - 3.1beta06, Tunnelblick will not recognize any **running** "when computer starts" configurations. Five to ten seconds after you start Tunnelblick, they will be identified as unknown OpenVPN processes and you will be given the choice to leave them alone or disconnect them. You should chose to disconnect them in this dialog and then manually connect them in Tunnelblick. (You do not need to do this immediately, but you will not be able to control them with Tunnelblick. The dialog will appear each time you start Tunnelblick if these connections are still active.) This need only be done once, and is not necessary if there are no "when computer starts" configurations that are connected at the time you update.



  * Updates to use OpenSSL 1.0.0c, which fixes several security vulnerabilities.

  * Searches for the icon set folder in Tunnelblick.app/Contents/Resources/Deploy and then in /Library/Application Support/Tunnelblick/Shared before defaulting to the version in Tunnelblick.app/Contents/Resources.

  * Fixes bug that caused an unneeded folder (dmgFiles) to be built into Tunnelblick.app/Contents/Resources.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS