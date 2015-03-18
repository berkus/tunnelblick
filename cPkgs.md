

## Introduction ##
A Tunnelblick VPN Configuration (a "Configuration") is a folder with an extension of .tblk that contains information about one or more VPN configurations.
  * Configurations provide a convenient way to distribute VPN configurations separately from the Tunnelblick application itself.
  * Configurations may be installed to be private to a single user or shared by all users of the computer.
  * Configurations may be automatically installed when Tunnelblick is installed.
  * Configurations may contain identification and version information to assist in version control.
  * Configurations may contain scripts that are run at particular points in the connection process.
  * Installing a Configuration requires a computer administrator username/password (as does Tunnelblick installation).
  * The configuration file of a Configuration that is private may be edited. The configuration file of a Configuration that is shared may only be examined.

Configurations are available in Tunnelblick 3.1 and up. Some features of Configurations described in this document may only be available on Tunnelblick 3.4beta30 and higher.

**Configurations must be installed before they can be used.** Install a Configuration by double-clicking it. (The Tunnelblick application must have been installed _before_ the Configuration is double-clicked.)

## Creation and Modification ##

See [Creating and Installing a Tunnelblick VPN Configuration](cConfigT#Creating_and_Installing_Tunnelblick_VPN_Configuration.md) and [Modifying a Tunnelblick VPN Configuration](cConfigT#Modifying_a_Tunnelblick_VPN_Configuration.md).

## Installation ##
A Configuration is installed by double-clicking it. A configuration can be installed automatically when Tunnelblick is installed from a disk image or a folder expanded from a .zip file (see [Automatic Installation](cPkgs#Automatic_Installation.md)).

If there is only one OpenVPN configuration file inside a .tblk, a single Configuration will be installed and will have the name of the .tblk -- the name of the configuration file will be ignored.

If there is more than one OpenVPN configuration file inside a .tblk, a Configuration will be installed for each configuration file, and will have the name of the configuration file.

When a Configuration is installed, it's contents are copied and arranged in a special way and the copy is secured by setting the ownership and permissions on the copy's contents.

Unless specified otherwise in an [Info.plist](#Info.plist.md), when a Configuration is installed the user will be asked whether the Configuration is to be shared or private (for only that user). Configurations to be shared are copied to `/Library/Application Support/Tunnelblick/Shared`; Configurations to be kept private are copied to `~/Library/Application Support/Tunnelblick/Configurations`.

## Nested Configurations ##
"Nested" Configurations make it easy to distribute many configurations in a single file.

Configurations may be nested one level deep. That is, a Configuration may contain within it other Configurations (and may also contain OpenVPN configuration files that are not in a Configuration). When such a Configuration is installed, everything within it is installed. The Configurations within a Configuration may not themselves include Configurations, however -- only one level of included Configurations is allowed.

## Format ##
Tunnelblick Configurations are folders with an extension of ".tblk". The extension causes OS X to treat the folder as a "package" -- in most cases it is treated as if it were a single file. To look at the contents of a package (i.e. inside what was the folder), control-click or right-click the package and select "Show Package Contents".

**Before installation**, a Tunnelblick VPN Configuration can contain files and folders including:
  * An Info.plist file (see [Info.plist](#Info.plist.md)).
  * One or more "nested" Tunnelblick VPN Configurations
  * One or more OpenVPN configurations (files with .ovpn or .conf extensions).
  * One or more key, certificate, or script files.

If configurations are in subfolders, the structure of the subfolders will be replicated when the configurations are installed.

**After installation**, the contents of a Tunnelblick VPN Configuration are arranged as follows. Before installation all files can be arranged this way, or all files can be at the top level of the .tblk (that is, without the "Contents/Resources" structure).

```
    sample.tblk/
        Contents/
            (Optional) Info.plist
            Resources/
                config.ovpn, containing OpenVPN configuration information
                (Optional) up/down scripts
                (Optional) Tunnelblick scripts
                (Optional, deprecated scripts) up.sh, down.sh, nomonitor.up.sh, and/or nomonitor.down.sh
                (Optional) key, certificate, and/or other script files
```

## Info.plist ##
Info.plist is optional. If it exists, it must be an [OS X property list](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html#//apple_ref/doc/uid/10000048-CJBGDEGD) file, with keys from the following table. The only mandatory key is TBPackageVersion; all others are optional.
|Key|Description|Default|Examples|
|:--|:----------|:------|:-------|
|CFBundleIdentifier (**case-insensitive**)|A string that uniquely identifies the configuration and the individual or organization distributing the Configuration.|(None)|com.example.tbconfigs.config27a|
|CFBundleVersion |A string representing the version number that is used to determine later/earlier versions of the Configuration (see [CFBundleIdentifier Conflicts](cPkgs#CFBundleIdentifier_Conflicts.md)). The string must consist of a major version number, optionally followed by a decimal point and a minor version number, optionally followed by a decimal point and a bugfix version number|(None)|1.16.4|
|CFBundleShortVersionString|A string to display as the version (in Get Info, for example)|(None)|1.6 Test 3|
|TBPackageVersion (**required**)|A string with the Configuration version number|1 |The string "1" (without the quotation marks)|
|TBReplaceIdentical|A string specifying whether to install the Configuration over a Configuration with the same CFBundleIdentifier. Must be "yes", "no", "ask", or "force" (without the quotation marks)|ask|yes|
|TBSharePackage|A string specifying whether to install the Configuration as shared or private, or to ask the user. Must be "shared", "private", or "ask" (without the quotation marks)|ask|ask|
|TBKeepExistingFilesList|An array of filenames. Used for a configuration that is replacing an existing configuration. Each array entry is the filename (without path information) of a file that is not in the configuration being installed and which should be left as it is in the existing configuration that is being replaced. A single **`*`** character in the filename will match any number of any characters in the name. (Available in 3.4beta33 build 3908 and higher.)|(None)|client.key, client`*`.key, `*`.key, client.`*`, client`*`, `*`|
|TBPreference|See [Preferences](cPkgs#Preferences.md)|  |TBPreferenceuseDNS|
|TBAlwaysSetPreference|See [Preferences](cPkgs#Preferences.md)|  |TBAlwaysSetPreferenceuseDNS|
|TBUninstall|If present (with any value), the .tblk will be uninstalled|  |  |

## Preferences ##
A Configuration's Info.plist may also optionally contain entries (strings, numbers, and booleans) with keys that start with "TBPreference" or "TBAlwaysSetPreference". The entries are preferences for the configuration. Each entry will be copied to the user's regular preferences each time Tunnelblick loads or uses the Configuration (when Tunnelblick is launched or the Configuration is installed or connected). "TBPreference" items are copied only if the preference is not already set, so they are for initial settings that a user is allowed to override. "TBAlwaysSetPreference" items always are copied, so the user is, in effect, not allowed to override them. When the entries are copied, "TBPreference" or "TBAlwaysSetPreference"is replaced with the display name of the Configuration. Note that the "autoConnect" option triggers a connection when Tunnelblick is started, so a configuration with "TBPreferenceautoConnect" is not connected automatically when it is installed, but is connected automatically the next time Tunnelblick is launched. _Note: "TBAlwaysSetPreference" is only available in Tunnelblick 3.3beta10 and later._

In a Deployed version of Tunnelblick, the forced-preferences in Deploy will override any Configuration-specified preferences.

## Up/Down Scripts ##
If the Configuration contains up.tunnelblick.sh, down.tunnelblick.sh, up.sh, down.sh, nomonitor.up.sh, and/or nomonitor.down.sh, those scripts will be used instead of Tunnelblick's standard scripts, or scripts in Deploy, when connecting with the Configuration and "Set nameserver" is selected for the Configuration's configuration.

For backward compatibility, scripts other than up.tunnelblick.sh and down.tunnelblick.sh will be used if they exist.

In a Deployed version of Tunnelblick, a Configuration's up/down scripts will override the corresponding scripts in Deploy.

## Tunnelblick Scripts ##
If the Configuration includes pre-connect.sh, post-tun-tap-load.sh, connected.sh, reconnecting.sh, post-disconnect.sh scripts, they will be executed (as root) at the corresponding point in the connection process. This allows manipulation of kexts and/or the network configuration and user notification of events. (If the scripts load special kexts, you can use the "-doNotLoadTapKext" and "-doNotLoadTunKext" preferences to cause Tunnelblick to not try to load its own kexts.) post-tun-tap-load.sh, connected.sh, and reconnecting.sh are available in Tunnelblick 3.2beta02 and later only. See [Using Scripts](cUsingScripts.md) for more details.

## Automatic Installation ##
When Tunnelblick is installed by double-clicking a Tunnelblick.app that is not in /Applications, all Configurations in the "auto-install" and ".auto-install" folders that are in the same folder that contains the Tunnelblick.app being installed are installed (subject to [CFBundleIdentifier Conflicts](cPkgs#CFBundleIdentifier_Conflicts.md) and [Name Conflicts During Installation](cPkgs#Name_Conflicts_During_Installation.md)).

The "auto-install" and ".auto-install" folders can also contain a file named "preferences.plist". It may contain a "set-only-if-not-present" key and/or a "always-set" key. The value for each key should be a dictionary containing preferences to be set under the specified conditions.

Thus, one can construct a disk image (or a .zipped folder) which contains Tunnelblick.app and an "auto-install" folder containing configurations and preferences to be installed along with Tunnelblick.

## CFBundleIdentifier Conflicts ##
On automatic or manual installation of a Configuration, if a Configuration with an identical CFBundleIdentifier is already installed:
  * If the new Configuration's "TBReplaceIdentical" is "no", the Configuration will not be installed.
  * If the new Configuration's "TBReplaceIdentical" is "yes", the existing Configuration will be replaced without notifying the user if it has an equal or higher "CFBundleVersion" than the existing installed Configuration. If it has a lower "CFBundleVersion", the Configuration will not be installed.|(None)|client.key, client**.key, client.**|
|:-----|:----------------------------------|
  * If the new Configuration's "TBReplaceIdentical" is "force", the existing Configuration will be replaced without notifying the user.
  * If the new Configuration's "TBReplaceIdentical" is "ask", the existing Configuration will be replaced only after getting the user's consent.

When an existing Configuration is replaced, the new copy takes the display name of the existing version, regardless of the name of the new Configuration. Thus, the new version will inherit the existing version's preferences and Keychain items.

## Name Conflicts During Installation ##
If the display name of a Configuration is the same as the name of an existing .ovpn or .conf file or  an existing Configuration that has a different CFBundleIdentifier, the user will be asked to rename the Configuration or cancel the installation.

## Name Conflicts After Installation ##
Configurations are displayed from
  * `Tunnelblick.app/Contents/Resources/Deploy`
  * `/Library/Application Support/Tunnelblick/Shared/*.tblk`
  * `/Library/Application Support/Tunnelblick/Shared/*.ovpn and *.conf`
  * `~/Library/Application Support/Tunnelblick/Configurations/*.tblk``
  * `~/Library/Application Support/Tunnelblick/Configurations/*.ovpn and *.conf`
in that order. If a display name matches an earlier display name, the later configuration will be ignored and only the earlier display name will be displayed, making only the earlier configuration available.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS