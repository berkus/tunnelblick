

&lt;hr&gt;


<font size='3'><b><a href='http://code.google.com/p/tunnelblick/downloads/detail?name=Tunnelblick_3.1beta18.dmg'>Download Tunnelblick 3.1beta18</a></b></font>


&lt;hr&gt;



**[Full Release Notes](RlsNotes.md)**

## What's New in Tunnelblick 3.1beta18 (Changes from 3.1beta16) ##
  * <font color='red'><b>IMPORTANT NOTE FOR THOSE USING "WHEN COMPUTER STARTS" WITH EARLIER BETA VERSIONS:</b></font> The first time that you update to Tunnelblick 3.1beta08 or above from 3.1beta02 - 3.1beta06, Tunnelblick will not recognize any **running** "when computer starts" configurations. Five to ten seconds after you start Tunnelblick, they will be identified as unknown OpenVPN processes and you will be given the choice to leave them alone or disconnect them. You should chose to disconnect them in this dialog and then manually connect them in Tunnelblick. (You do not need to do this immediately, but you will not be able to control them with Tunnelblick. The dialog will appear each time you start Tunnelblick if these connections are still active.) This need only be done once, and is not necessary if there are no "when computer starts" configurations that are connected at the time you update.



  * When there are more than eight configurations, the Details… window changes to display a list of connections on the left side and a single tab with the log and controls on the right. This was done because of OS X problems when there are a large numbers of tabs. The 'maximumNumberOfTabs' preference specifies the maximum number of tabs to display; if there are more than that many configurations, the display will change as described above. The preference defaults to 8. Set this preference to 0 to always show configurations in a list on the left.

  * Streamlines installation by double-clicking to have only one dialog box explaining what will be installed and asking for admin username/password.

  * Fixes bug which prevented Standard users from installing Tunnelblick by double-clicking.

  * Fixes bugs in automatic installation of .tblks when installing Tunnelblick.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS