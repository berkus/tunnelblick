

&lt;hr&gt;


<font size='3'><b><a href='http://tunnelblick.googlecode.com/files/Tunnelblick_3.1beta12.dmg'>Download Tunnelblick 3.1beta12</a></b></font>


&lt;hr&gt;



**[Full Release Notes](RlsNotes.md)**

## What's New in Tunnelblick 3.1beta12 (Changes from 3.1beta10) ##
  * <font color='red'><b>IMPORTANT NOTE FOR THOSE USING "WHEN COMPUTER STARTS" WITH EARLIER BETA VERSIONS:</b></font> The first time that you update to Tunnelblick 3.1beta08 or above from 3.1beta02 - 3.1beta06, Tunnelblick will not recognize any **running** "when computer starts" configurations. Five to ten seconds after you start Tunnelblick, they will be identified as unknown OpenVPN processes and you will be given the choice to leave them alone or disconnect them. You should chose to disconnect them in this dialog and then manually connect them in Tunnelblick. (You do not need to do this immediately, but you will not be able to control them with Tunnelblick. The dialog will appear each time you start Tunnelblick if these connections are still active.) This need only be done once, and is not necessary if there are no "when computer starts" configurations that are connected at the time you update.



  * Includes Italian localization thanks to Pierpaolo Gulla (Grazie!).

  * Implements a single, system-wide keyboard shortcut (command-option-F1 by default) to expose the Tunnelblick menu.
    * This make it possible to use Tunnelblick with only a keyboard.
    * The keyboard shortcut may be used whenever Tunnelblick is running - it does not need to be the front-most application.
    * A new submenu of the Options submenu has been added to allow the key to be changed to any of the function keys from F1 through F12. The display of the new menu item is inhibited if the 'doNotShowKeyboardShortcutSubmenu' preference is set to TRUE.
    * Two new unsigned integer preferences: 'keyboardShortcutKeyCode' contains the virtual keycode for the key, and 'keyboardShortcutModifiers' contains the code for the modifier keys.

  * No longer displays Tooltips by default. They are displayed only if the 'showTooltips' preference is set to TRUE. This is necessary because tooltips on menu items interfere with the proper operation of VoiceOver, OS X's built-in screen access solution.

  * Terminates faster if going to sleep or if no unknown OpenVPN processes exist and no 'when computer starts' configurations are connected.

  * Works around the following OpenVPN bug: when in the 'RESOLVE' state, the OpenVPN process ignores the first SIGTERM (via kill or management interface) and delays termination for tens of seconds after a second or subsequent SIGTERM. Works around this by warning the user that this is happening, then repeatedly sending SIGTERM and, after a timeout period (default is 180 seconds), considering the connection closed even if OpenVPN doesn't acknowledge the closing. Two new preferences specify the time in seconds between sending SIGTERMs ('openvpnTerminationInterval') and the total maximum time in seconds to wait before considering the connection closed ('openvpnTerminationTimeout').

  * Logs errors trying to create or update 'Launch Tunnelblick' in the private configurations folder.

  * Fixes bugs (race conditions) when the log view is being updated and when MenuExtras are added.

  * Fixes bug with placement of the 'when computer starts' radio button in non-English versions of Tunnelblick.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS