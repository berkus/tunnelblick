Starting with Build 1326, the build process for Tunnelblick specifies the view options, icon positions, and background image that the user sees upon opening Tunnelblick.dmg. These settings are contained in the "tunnelblick/dmgFiles" folder, which contains three items:

  * The "tunnelblick/dmgFiles/dotDS\_Store" file is a .DS\_Store file copied from a volume which has view options, icon positions, and a background image set up the way we want the Tunnelblick .dmg to appear. The file is copied to the staging folder ("/tunnelblick/build/Release/Tunnelblick"), and the copy there is renamed ".DS\_Store" and set to be invisible in the Finder, before the .dmg is created from the staging folder.

  * The "tunnelblick/dmgFiles/background" folder contains the "background.png" file which is used as a background for the .dmg when it is opened in the Finder. The folder and its contents are copied to the staging folder, and the copy of the folder in the staging folder is set to be invisible in the Finder, before the .dmg is created from the staging folder.

  * The "background.rtf" file is not used directly in the creation of the .dmg. Instead, it provides an easy way to create the text-based background image. It is an RTF document which can be easily edited in SimpleText. A screenshot of it can then taken to provide the "background.png" file that is used as a background image when the .dmg is opened in the Finder. This is done so that additional translations can be added, corrections made, etc. (Don't forget to turn off spell checking in SimpleText when taking the screenshot, so wavy red underlines don't appear in it!)

## MODIFYING THE BACKGROUND IMAGE ##

To modify the background image, simply edit "background.rtf", take a screenshot (using Command-Shift-4) starting from the upper-left corner of the editing window, rename the screenshot to "background.png", and copy it into "tunnelblick/dmgFiles/background", overwriting the old version.

## ADDING/REMOVING CONTENT OR MODIFYING THE LAYOUT OF ICONS OR VIEW OPTIONS ##

Note: According to http://www.araelium.com/dmgcanvas:
> "In Mac OS X Snow Leopard, disk images created with background images do not display properly on Mac OS X Leopard and earlier. This is because of a change in Finder itself that affects all disk images created on Snow Leopard."

However, setting the size of the window on Tiger/Leopard doesn't set it for Snow Leopard. So you need to use both Tiger/Leopard and Snow Leopard to adjust everything the way you want it!

Do the following **in Leopard or Tiger**:
  1. Use Disk Utility to convert Tunnelblick.dmg to a read/write image named "TunnelblickRW.dmg". ("Convert" creates a new copy without disturbing the original.)
  1. Double-click the read-write image and then double-click the resulting Tunnelblick volume to open a window for it in the Finder.
  1. Manipulate the window to add or remove files, change view options and icon positions, etc. as desired.
  1. Close the window.
  1. Eject the Tunnelblick volume
  1. Log out and log back in again or restart your computer. (The logout/login or restart seems to be necessary to flush the Finder's cache of data to the the .DS\_Store file on the volume.)

Then, do the following **in Snow Leopard:**
  1. Double-click the read-write image and then double-click the resulting Tunnelblick volume to open a window for it in the Finder.
  1. Manipulate the to resize it if necessary.
  1. Close the window.
  1. Eject the Tunnelblick volume
  1. Log out and log back in again or restart your computer. (The logout/login or restart seems to be necessary to flush the Finder's cache of data to the the .DS\_Store file on the volume.)
  1. Use Disk Utility to convert TunnelblickRW.dmg to a "compressed" disk image named "TunnelblickC.dmg".
  1. Double-click TunnelblickC.dmg and verify that the window layout, view options, etc. are as desired.
  1. Use the following Terminal commands to (A) copy the volume's .DS\_Store file and (B) make it visible. (Tip: drag and drop a item's icon from a Finder window to anywhere in the Terminal window to insert the absolute path to that item, followed by a space, at the Terminal window's insertion point.)

> `cp -p /Volumes/Tunnelblick/.DS_Store` _path-to-dmgFiles/dotDS\_Store_

> `setfile -a v` _path-to-dmgFiles/dotDS\_Store_

> Example assuming the source code is in a folder named "TB" in a user's Documents folder:

> `cp   -p   /Volumes/Tunnelblick/.DS_Store   /Users/joe/Documents/TB/tunnelblick/dmgFiles/dotDS_Store`

> `setfile   -a   v   /Users/joe/Documents/TB/tunnelblick/dmgFiles/dotDS_Store`

Note: The 'setfile' command is part of Apple's Developer Tools (see [Building from Source](cBuild.md)).

---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS