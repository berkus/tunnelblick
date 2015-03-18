## Icon Animation ##
Tunnelblick displays the VPN connection status using the Tunnelblick icon in the Status Bar. The Tunnelblick icon is usually located next to the Spotlight icon, but if the "placeIconInStandardPositionInStatusBar" preference is set, the icon will be placed to the left of the icons being displayed at the time Tunnelblick is launched.

  * The Tunnelblick icon indicates a closed tunnel (i.e., no VPN connection) with a "dark" tunnel:

> ![http://tunnelblick.googlecode.com/files/using-tunnelblick-closed-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-closed-2010-02-04.png)

  * An open tunnel (i.e., a VPN connection) is indicated with a "light" tunnel:

> ![http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-open-2010-02-04.png)

  * When a tunnel (VPN connection) is in the process of being established or taken down, the icon is animated, going from "dark" to "light" and back repeatedly.

## Icon Sets ##
A folder containing a set of these images meant to be used together is called an "icon set".

Tunnelblick comes with one folder containing the standard icon set built-in. It is located within the Tunnelblick application itself, at
> Tunnelblick.app/Contents/Resources/IconSets/TunnelBlick.TBMenuIcons.

When Tunnelblick is launched, it looks for an icon set to use in three places, in the following order:
  1. Tunnelblick.app/Contents/Resources/Deploy/IconSets/TunnelBlick.TBMenuIcons;
  1. /Library/Application Support/Tunnelblick/Shared/IconSets/TunnelBlick.TBMenuIcons; and
  1. Tunnelblick.app/Contents/Resources/IconSets/TunnelBlick.TBMenuIcons.

Each icon set must be accompanied by an icon set named with a prefix of "large-". That icon set should contain icons that are three times larger than the normal icons, in both width and height. Thus the "large" icons should be 54 x 48 pixels (since the normal icons are 18 x 16 pixels).

Note: The "menuIconSet" preference, if present, specifies the name of the folder (within the "IconSets" folder) that contains the icon set to be used. If not present, this defaults to "TunnelBlick.TBMenuIcons".

## Custom Icon Sets ##
Custom icon sets can be used to override the standard icon set.

First, create a folder named "TunnelBlick.TBMenuIcons" containing the images. The images must be named:
  * "open.png": this is the icon used to indicate an open tunnel (a VPN connection is active)
  * "closed.png": this is the icon used to indicate a closed tunnel (no VPN connection is active)
  * "1.png", "2.png", "3.png", etc.: these icons are used in sequence to indicate a transition from open to closed or closed to open.

Next, create a folder named "large-TunnelBlick.TBMenuIcons" containing larger images.

Next, either
  1. Replace the Tunnelblick.app/Contents/Resources/IconSets/TunnelBlick.TBMenuIcons folder with your folder (and the large-TunnelBlick.TBMenuIcons folder with your "large-" folder) ; or
  1. Create an "IconSets" folder, place your folders inside it, and place it in either
    * Tunnelblick.app/Contents/Resources/Deploy; or
    * /Library/Application Support/Tunnelblick/Shared.

What happens to your icon set when Tunnelblick is updated depends on where you put it:
  * If it is in Tunnelblick.app/Contents/Resources/IconSets, it will be replaced with the standard icon set;
  * If it is in Tunnelblick.app/Contents/Resources/Deploy, it will be restored after Tunnelblick is updated;
  * If it is placed in /Library/Application Support/Tunnelblick/Shared, it will not be affected when Tunnelblick is updated.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS