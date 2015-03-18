## Generating an HMAC Signature ##

If you are setting up your own OpenVPN server and clients, using the OpenVPN "--tls-auth" option is [recommended](https://openvpn.net/index.php/open-source/documentation/howto.html#security) as one way of "hardening" the security of your OpenVPN setup. The option requires an HMAC signature file, which you can generate on your Mac using the OpenVPN program included in Tunnelblick.



&lt;hr&gt;


## For Experts: Commands to Generate an HMAC Signature ##

First, install the latest beta version of Tunnelblick, then use the following commands:

```
     cd ~/Library/Application\ Support/Tunnelblick/easy-rsa/keys
     /Applications/Tunnelblick.app/Contents/Resources/openvpn/openvpn-2.3.4/openvpn --genkey --secret ta.key
     cd ..
```

Replacing "2.3.4" above with the version of OpenVPN that you want to use to create the key, if it isn't "2.3.4". (OpenVPN version 2.3.4 is included in Tunnelblick 3.4beta36, the latest version as of this writing.)



&lt;hr&gt;


## Very Detailed Instructions to Generate an HMAC Signature ##

You need to figure out which version of OpenVPN to use to generate the key -- most versions of Tunnelblick include at least two versions of OpenVPN. Probably you want to use the latest version of Tunnelblick and the latest version of OpenVPN.

  1. Make sure you have downloaded the latest beta version of Tunnelblick and installed it by double-clicking the Tunnelblick icon in the disk image.

> 2. Open a Finder window, find the /Applications folder, and find Tunnelblick.app in /Applications. Control-click on Tunnelblick.app and click on "Show Package Contents". That will show a "Contents" folder. Double-click "Contents", double-click "Resources", then double-click "openvpn". That "openvpn" folder will contain a folder for each version of OpenVPN that your copy of Tunnelblick includes (and a symlink named "default" which you can ignore).

> 3. Double-click the folder with the latest name ("openvpn-2.3.4", currently). You will see two items, "openvpn" and "openvpn-down-root.so".

> 4. Open a Terminal window with the easy-rsa folder (for example, by using the "Open easy-rsa in Terminal" button on the "Utilities" panel of Tunnelbick's "VPN Details…" window).

> 5. Type the following into the Terminal window:
```
     cd keys
```
> > followed by the "Enter" or "Return" key, so "keys" is the working directory.


> 6. Drag the "openvpn" file from the Finder window to the Terminal window. That will copy the full path of the "openvpn" file and a space to the Terminal window.

> 7. Copy/paste the following to the Terminal window:
```
     --genkey --secret ta.key
```
> > At that point, the line in Terminal will look like the following, with X.Y.Z replaced with digits:
```
     /Applications/Tunnelblick.app/Contents/Resources/openvpn/openvpn-X.Y.Z/openvpn --genkey --secret ta.key
```


> 8. Press the "enter" or "return" key to start the key generation.

> 9. When key generation is complete, type
```
     cd ..
```
> > to return to the easy-rsa folder.

The "ta.key" file will be in the "keys" folder:
```
     /Users/YOUR-USERNAME/Library/Application\ Support/Tunnelblick/easy-rsa/keys
```


---

### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS