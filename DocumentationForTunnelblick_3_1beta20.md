

&lt;hr&gt;


<font size='3'><b><a href='http://code.google.com/p/tunnelblick/downloads/detail?name=Tunnelblick_3.1beta20.dmg'>Download Tunnelblick 3.1beta20</a></b></font>


&lt;hr&gt;



**[Full Release Notes](RlsNotes.md)**

## What's New in Tunnelblick 3.1beta20 (Changes from 3.1beta18) ##
  * <font color='red'><b>IMPORTANT NOTE FOR THOSE USING "WHEN COMPUTER STARTS" WITH EARLIER BETA VERSIONS:</b></font> The first time that you update to Tunnelblick 3.1beta08 or above from 3.1beta02 - 3.1beta06, Tunnelblick will not recognize any **running** "when computer starts" configurations. Five to ten seconds after you start Tunnelblick, they will be identified as unknown OpenVPN processes and you will be given the choice to leave them alone or disconnect them. You should chose to disconnect them in this dialog and then manually connect them in Tunnelblick. (You do not need to do this immediately, but you will not be able to control them with Tunnelblick. The dialog will appear each time you start Tunnelblick if these connections are still active.) This need only be done once, and is not necessary if there are no "when computer starts" configurations that are connected at the time you update.



  * Removed confusing question when Tunnelblick is launched and foo.tap and/or foo.tun (old Tunnelblick kexts) are loaded. The question asked if foo.tun and foo.tap should be unloaded. Now they are unloaded only as needed to make a connection: foo.tap is unloaded if net.tunnelblick.tap is being loaded for the connection, and foo.tun is unloaded if net.tunnelblick.tun is being loaded for the connection. The 'skipAskingToUnloadFooKexts' preference is no longer used. To override Tunnelblick's automatic loading of the tun or tap kexts required for a connection, see the following per-configuration [Preferences](wPrefs.md): "-doNotLoadTunKext", "-doNotLoadTapKext", "-loadTunKext", and "-loadTapKext".


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS