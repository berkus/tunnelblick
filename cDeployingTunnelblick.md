**For help configuring and using Tunnelblick, see [Using Tunnelblick](UsingTunnelblick.md) and the [Tunnelblick Discussion Group](http://groups.google.com/group/tunnelblick-discuss).**

This document contains the following sections:



<font color='red'><strong>Note: Starting with Tunnelblick 3.3beta22, Deployed versions of Tunnelblick must be <a href='cRebranding.md'>rebranded</a>. The rebranded version is referred to as "Rebranded.app" or "Rebranded.dmg" throughout this document.</strong></font>

## What is a Deployed Version? ##
A deployed version of Tunnelblick is a customized version of Tunnelblick.app which can include everything necessary to install and run Tunnelblick and connect to one or more VPNs. In particular, it may include one or more OpenVPN configuration files, and, usually, certificate and key files for authentication. It can also include shell scripts and text that will appear in Tunnelblick's "about" window, and can specify user preferences that are forced to particular values and are read-only.

## How it Works ##
You create a deployed version of Tunnelblick by:
  1. [Building your own binary](.md) of Tunnelblick from [rebranded](cRebranding.md) source code.
  1. Putting a "Deploy" folder into the `Contents/Resources` folder of your Rebranded.app. `Deploy` can contain any one or a combination of configuration files, certificate and key files, up/down scripts, and a "forced-preferences.plist" file. Since `Deploy` and its contents can not be modified by a non-administrator user, this is a secure way to ensure that your users do not tamper with any settings that you wish to protect.

If `Contents/Resources/Deploy` exists, Rebranded.app's behavior changes:
  * If `Deploy` contains one or more .conf or .ovpn files, Rebranded uses it, instead of `~/Library/Application Support/Rebranded/Configurations`, for configuration files. When a connection is attempted, the log entry that Rebranded puts in the OpenVPN log in the "VPN Details…" window will contain "from Deploy" if `Deploy` is being used for configuration files.

  * If `Deploy` contains a "forced-preferences.plist" file, Rebranded will use the preferences in it to override corresponding preferences in the user's `~/Library/Preferences/net.rebranded.rebranded.plist`. See [Forced Preferences](Forced_Preferences.md) for details. See [Preferences](Preferences.md) for a list of all preferences.

## Signed vs. Unsigned Versions ##
A copy of Rebranded can be signed or unsigned. All non-Deployed versions of Rebranded should be signed versions, but signing interferes with some Deployed configurations. Use an unsigned version if users will be able to store usernames/passwords/passphrases in the Keychain and the Deploy folder is added after the Rebranded build process (which is where signing is usually done). See [Tunnelblick and Digital Signatures](cDigitalSignatures.md) for details.

## Forced Preferences ##
Preferences in `Deploy/forced-preferences.plist` override the user's normal preferences located in `~/Library/Preferences/net.rebranded.rebranded.plist`. Wildcards can be used to simplify the specification of forced preferences for multiple configurations.

Forced preferences are implemented as follows:
  1. If a forced preference has the same name as a normal preference, the forced preference is used instead of the normal preference.
  1. If a forced preference begins with an asterisk ("`*`") and the rest of the forced preference matches the end of a normal preference, it is used instead of the normal preference.
  1. Otherwise the normal preference is used, or the default if there is no normal preference.

A forced preference consisting only of an asterisk ("`*`") will be ignored.

For example, with forced preferences of `*useDNS`= TRUE and `config1useDNS` = FALSE, configuration `config1` will be forced to not use DNS, and all other configurations will be forced to use DNS. The user will not be able to change any `useDNS` preferences.

Another example: forced preferences of `*ABCuseDNS`= TRUE, `*DEFuseDNS`= FALSE, configuration `configABC` will be forced to use DNS, and `configDEF` will be forced to not use DNS. The user will be able to change `useDNS` preferences for other configurations, if any.

There are two **exceptions** to the way forced preferences work:
  * All forced preferences with a key beginning with "SU" are ignored. These preferences are used privately by Sparkle Updater, and should not be used. Tunnelblick provides preferences (which can be forced) which control the update process and override these Sparkle preferences.
  * Forcing the _config-name_-keychainHasPrivateKey and _config-name_-keychainHasUsernameAndPassword preferences -- regardless of value -- prevent the user from storing or using passphrases, usernames, or passwords for that configuration in the Keychain. Dialog boxes will not include a "Save to Keychain" checkbox, and any passphrases, usernames, and passwords in the Keychain will be ignored.

See [Preferences](Preferences.md) for a list of all preferences.

## What is Needed to Make a Deployed Version ##
To make a deployed version of Tunnelblick, you need a [rebranded](cRebranding.md) version of Tunnelblick and whatever is required to connect to your VPN.

To be more specific, you need:
  * A copy of the rebranded Tunnelblick .dmg file.
  * Optional: one or more OpenVPN configuration files, with extensions of ".ovpn" or ".conf".
  * Optional: certificate and key files for authentication.
  * Optional: shell script files, with extension ".sh", if you do not use Tunnelblick's "Set nameserver" feature. If you have shell files, they must have an extension of "sh"; otherwise they will not have execute permissions.
  * Optional: "about.html" file, containing text that will be displayed in Tunnelblick's "about" window.
  * Optional: "forced-preferences.plist" file, containing user preferences that you wish to override.
  * Optional: other files that you want your configuration file or scripts to be able to use.

## How to Make a Deployed Version ##
  1. Create a new folder on your Desktop and rename it "Deploy"
  1. Copy any of the optional files you wish to use into the "Deploy" folder
  1. Open the Rebranded .dmg file. A new Finder window will appear with (among other things) Rebranded.app
  1. Drag Rebranded.app to the Desktop (or some other place you will work with it). This is the copy you will modify to create your deployed version.
  1. Right-click on Rebranded.app, and click "Show Package Contents". A new Finder window will appear with a folder "Contents".
  1. Double-click on "Contents". The window will change to show several items. One of them is a folder, "Resources"
  1. Option-drag your "Deploy" folder and drop it onto "Resources" to copy the folder into "Resources"
  1. If you have one, copy your "about.html" file into "Resources"
  1. Close the window that contains "Resources"

That's it! You are done! your Rebranded.app has your new version of Tunnelblick with a `Deploy` folder containing everything that Rebranded needs for connection to your VPN.

## How to Use a Deployed Version ##
Using Rebranded is the same as using a non-deployed version, except:
  * You will not be asked for administrator credentials the first time you first connect to a VPN. (Because ownership and permissions on the configuration file(s) was secured the first time Rebranded was run on the computer.)
  * Anyone with access to /Applications can connect to its VPN(s) -- it can be accessed by any user of the computer, without requiring administrator credentials to set up secure configuration files in ~/Library/Application Support/Tunnelblick/Configurations -- because ~/Library/Application Support/Tunnelblick/Configurations is not used and the configuration files are shared by all users with access to /Applications.

## Creating a .zip File for Deployment ##
To create a .zip file of your new version of Tunnelblick:
  1. Right-click on your new version of Tunnelblick, and click "Compress Rebranded.app"
That's all. There is no step 2. Your .zip file has been created.

## Creating a .dmg File for Deployment ##
  1. Create a new folder on your Desktop and rename it "Rebranded"
  1. Copy whatever you want to include in the .dmg file into the folder, including your new version of Rebranded.app
  1. Open `/Applications/Utilities/Disk Utility`
  1. Chose "File", then "New", then "Disk Image from Folder"
  1. Select the folder you set up in steps 1. and 2. and click the "Image" button
  1. Type a name for your .dmg file, and select a location in which to store it
  1. Select "Image Format: compressed", and "Encryption: none"
  1. Click "Save"
Within a few moments, your .dmg file will be created.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS