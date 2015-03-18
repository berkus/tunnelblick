#### THIS IS A PROPOSAL. IT HAS NOT BEEN IMPLEMENTED AND IT IS PRELIMINARY AND SUBJECT TO CHANGE. ####
#### PLEASE DISCUSS THIS PROPOSAL IN [THIS THREAD](http://groups.google.com/group/tunnelblick-discuss/t/45f208097827043f) IN THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) ####



## Introduction ##

This proposal arose from a [recent thread](http://groups.google.com/group/tunnelblick-discuss/browse_thread/thread/6920e90bb46229f3) on the Tunnelblick Discussion Group. Please discuss this proposal in [this thread](http://groups.google.com/group/tunnelblick-discuss/t/45f208097827043f).

A Tunnelblick package is a folder with an extension of .tblk that contains information about one VPN configuration.
  * Packages provide a convenient way to distribute VPN configurations separate from the Tunnelblick application itself.
  * Packages may be installed to be shared by all users of the computer, or installed to be private to a single user.
  * Packages may contain identification and version information to assist in version control.
  * Packages may be automatically installed when Tunnelblick is installed by including them in the Tunnelblick disk image.
  * Installing a package "secures" it by setting ownership and permissions on its contents. Because of that, package installation requires a computer administrator username/password (as does Tunnelblick installation).
  * The configuration file in a package installed as private will be "shadow copied" to the boot drive if it is on a network volume or if the "Use Shadow Copies" preference is set.

Tunnelblick packages must be installed before they can be used.

The configuration file of a Tunnelblick package that is private may be edited. The configuration file of a Tunnelblick package that is shared may only be examined.

## Installation ##
Installation of a package can be done manually by double-clicking it or by dragging it to a Tunnelblick icon in Finder. (A package _cannot_ be dragged to the Tunnelblick icon in the Status Bar.) Installation can also be done automatically when Tunnelblick is installed from a disk image or certain other other volumes (see [Automatic Installation](PackagesProposal#Automatic_Installation.md)).

When a package is installed, it is copied and the copy is secured by setting ownership and permissions on the package's contents.

The installed package may be shared or private. Packages to be shared are copied to `/Library/Application Support/Tunnelblick/Shared`, and packages to be kept private are copied to `~/Library/Application Support/Tunnelblick/Configurations`.

## Package Format ##
Tunnelblick packages are folders with an extension of ".tblk". (OS X will treat the folder as a package because of the extension.) The contents of a Tunnelblick package should be arranged as follows:

```
    sample.tblk/
        Contents/
            Info.plist
            Resources/
                config.ovpn, containing OpenVPN configuration information
                (Optional) shell scripts: up.sh, down.sh, nomonitor.up.sh, and/or nomonitor.down.sh
                (Optional) key, certificate, and/or other shell script files
```
The configuration file must reside at the top level of /Resources and be named "config.conf".

The name of the _package_ (without ".tblk") is used as the display name of the configuration unless it conflicts with an existing name (see [Name Conflicts During Installation](PackagesProposal#Name_Conflicts_During_Installation.md)).

## Info.plist ##
Info.plist is optional. If it exists, it must be an OS X property list file, and may contain the following keys:
|Key|Description|Default|Examples|
|:--|:----------|:------|:-------|
|CFBundleIdentifier|A string that uniquely identifies the configuration and the individual or organization distributing the package.|(None)|com.example.tbconfigs.config27A|
|CFBundleVersion |A string representing the version number that is used to determine later/earlier versions of the package (see [CFBundleIdentifier Conflicts](PackagesProposal#CFBundleIdentifier_Conflicts.md)). The string must consist of a major version number, optionally followed by a decimal point and a minor version number, optionally followed by a decimal point and a bugfix version number|(None)|1.16.4|
|CFBundleShortVersionString|A string to display as the version (in Get Info, for example)|(None)|1.6 Test 3|
|TBPackageVersion|A string with the package version number|1 |The string "1" (without the quotation marks)|
|TBInstallWhenInstallingTunnelblick|A string specifying whether to install the package when the package is located on a disk image or other volume from which Tunnelblick cannot be used and Tunnelblick is installed by double-clicking Tunnelblick.app on the volume. Packages will be found if they are in the same folder as Tunnelblick.app or any subfolder of that folder, including invisible subfolders. Must be "yes", "no", or "ask" (without the quotation marks)|ask|no|
|TBReplaceIdentical|A string specifying whether to install the package over a package with the same CFBundleIdentifier. Must be "yes", "no", "ask", or "force" (without the quotation marks)|ask|yes|
|TBSharePackage|A string specifying whether to install the package as shared or private, or to ask the user. Must be "shared", "private", or "ask" (without the quotation marks)|ask|ask|
|TBPreference|See [Preferences](PackagesProposal#Preferences.md)|  |TBPreferenceuseDNS|

## Preferences ##
A package's Info.plist may also optionally contain entries (strings and booleans) with keys that start with "TBPreference". The entries are preferences for the configuration. If not already present (with any value), each entry will be copied to the user's regular preferences each time Tunnelblick loads the package (when Tunnelblick is launched or the package is added to the Configurations folder). When the entries are copied, "TBPreference" is replaced with the display name of the package. Note that the "autoConnect" option triggers a connection when Tunnelblick is started, so a configuration with "TBPreferenceautoConnect" is not connected automatically when it is installed, but rather is connected automatically the next time Tunnelblick is launched.

In a Deployed version of Tunnelblick, the forced-preferences in Deploy will override any package-specified preferences.

## Up and Down Scripts ##
If the package contains up.sh, down.sh, nomonitor.up.sh, and/or nomonitor.down.sh, those shell scripts will be used instead of Tunnelblick's standard scripts, or scripts in Deploy, when connecting with the package and "Set nameserver" is checked for the package's configuration.

In a Deployed version of Tunnelblick, a package's up/down scripts will override the corresponding scripts in Deploy.

## Automatic Installation ##
When Tunnelblick itself is installed (by double-clicking Tunnelblick.app when it is located on a disk image or other volume from which it cannot be used), all packages in the folder containing the Tunnelblick.app being installed, or a subfolder of it, that have "TBInstallWhenInstallingTunnelblick" set to "yes" are installed (subject to [CFBundleIdentifier Conflicts](PackagesProposal#CFBundleIdentifier_Conflicts.md) and [Name Conflicts During Installation](PackagesProposal#Name_Conflicts_During_Installation.md). If "TBInstallWhenInstallingTunnelblick" is set to "no", the package will not be installed. If "TBInstallWhenInstallingTunnelblick" is "ask", the user will be asked before installing the package.

## CFBundleIdentifier Conflicts ##
On automatic or manual installation of a package, if a package with an identical CFBundleIdentifier is already installed:
  * If the new package's "TBReplaceIdentical" is "no", the package will not be installed.
  * If the new package's "TBReplaceIdentical" is "yes", the existing package will be replaced without notifying the user if it has an equal or higher "CFBundleVersion" than the existing installed package. If it has a lower "CFBundleVersion", the package will not be installed.
  * If the new package's "TBReplaceIdentical" is "force", the existing package will be replaced without notifying the user.
  * If the new package's "TBReplaceIdentical" is "ask", the existing package will be replaced only after getting the user's consent.

When an existing package is replaced, the new copy takes the display name of the existing version. Thus, the new version will inherit the existing version's preferences and Keychain items.

## Name Conflicts During Installation ##
If the display name of a package is the same as the name of an .ovpn or .conf file (without the .extension) from Deploy, /Library/Application Support/Tunnelblick/Shared, or ~/Library/Application Support/Tunnelblick/Configurations, or is the same as the display name of an existing package that has a different CFBundleIdentifier, the user will be asked to rename the package or cancel the installation;

## Name Conflicts After Installation ##
Configurations are displayed from
  * `Tunnelblick.app/Contents/Resources/Deploy`
  * `/Library/Application Support/Tunnelblick/Shared/*.tblk`
  * `/Library/Application Support/Tunnelblick/Shared/*.ovpn and *.conf`
  * `~/Library/Application Support/Tunnelblick/Configurations/*.tblk``
  * `~/Library/Application Support/Tunnelblick/Configurations/*.ovpn and *.conf`
in that order. If a display name matches an earlier display name, the later configuration will be ignored and only the earlier display name will be displayed, making only the earlier configuration available.

## Comparing Tunnelblick Packages and Deployed Versions of Tunnelblick ##
  * Deployed versions may have multiple configurations
  * Each package may have only one configuration

  * Configurations in two Deployed versions may not be combined.
  * Configurations in Deployed versions may optionally be combined with packaged and non-packaged configurations.
  * Configurations in packages are always combined with non-packaged, non-deployed configurations.

  * Deployed versions contain configurations within Tunnelblick.app
  * Packages are copied to ~/Library/Application Support/Tunnelblick/Configurations or /Library/Application Support/Tunnelblick/Shared

  * Deployed versions use "forced-preferences.plist" to force any Tunnelblick preference. The user cannot change the forced preferences. Wildcards may be used to specify preferences for multiple configurations.
  * Packages use Info.plist to provide default values for preferences of only that configuration. The user may change the preferences. No wildcards are allowed.

  * The Deploy folder is backed up each time Tunnelblick is launched if contents of Deploy have changed. The Deploy folder is restored from the backup if a Tunnelblick which does not contain the Deploy folder is launched from the same location. This means that once a Deployed version is launched and the backup is created, the launch of a "fresh" copy of Tunnelblick (one without a Deploy folder) from the same location will change that "fresh" version into a Deployed version. This is how the built-in updater can update Tunnelblick without losing the Deploy folder. If the updated "fresh" version of Tunnelblick contains Deploy, that (presumably new) version of Deploy will replace the old version (and then be backed up).
  * No backups of a package are created. However, note that the installation of a package involves copying the package, leaving the original unchanged.

  * Deployed versions ask for a computer administrator username/password only once, on the first launch of Tunnelblick. At that time, the program itself and all Deployed configurations are secured.
  * Non-deployed versions ask for  a computer administrator username/password on the first launch of Tunnelblick, when a package is installed, and the first time each non-packaged individual configuration is used.

  * Deployed versions of Tunnelblick allow an arbitrary arrangement of configuration files, folders, and subfolders within Deploy.
  * Packages are highly structured and require exactly one configuration file with a specific name.

  * In Deployed versions: key, certificate, script etc. files are referred to in the configuration file relative to /Deploy.
  * In packages: key, certificate, script etc. files are referred to in the configuration file relative to /Resources.

  * Packages may contain identifier and version information that will be used by Tunnelblick to manage updates.
  * Although Deployed versions may contain identifier or version information, Tunnelblick does not use that information.

## Document History ##
  * 2010-03-16
    * Document created
  * 2010-03-20
    * Changed Info.plist item for installation options, clarified language, reorganized
  * 2010-03-21
    * Clarified section about naming conflicts
  * 2010-03-25
    * Changed some Info.plist entries, added ability to install to shared location, added note about shadow copies, and made minor edits.
  * 2010-03-29
    * Relaxed requirements for Info.plist and made other minor edits
  * 2010-04-11
    * Removed the TBDisplayName Info.plist entry and made the .tblk structure more highly specified.
  * 2010-04-15
    * Changed config.conf to config.ovpn, and added up/down scripts within the package.
  * 2010-04-16
    * Minor wording change for clarification.
  * 2010-04-25
    * Clarified search path for installable packages on a disk image.
    * Changed default CFBundleIdentifier to "(None)".

#### PLEASE DISCUSS THIS PROPOSAL IN [THIS THREAD](http://groups.google.com/group/tunnelblick-discuss/t/45f208097827043f) IN THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) ####