**This  document describes how to create a deployed version of Tunnelblick and was last modified 2010-02-23.** It reflects the behavior of Tunnelblick built from the [r412](https://code.google.com/p/tunnelblick/source/detail?r=412) source code.

<font color='red'>Tunnelblick versions 3.3beta22 and higher CANNOT BE CREATED THIS WAY AND DO NOT BEHAVE LIKE EARLIER VERSIONS!</font>

Until this page is updated, please note that:
  * Only ["rebranded"](cRebranding.md) versions of Tunnelblick can be Deployed.
  * All Deployed versions must contain all configurations. The Deploy folder is not restored from a backup if a "plain" (i.e. non-Deploy) copy is installed over, or updates, a Deployed version.
  * Each configuration in /Deploy must be a Tunnelblick VPN Configuration (".tblk"), and must be structured as described in the [Format](cPkgs#Format.md) section of the [".tblk" Details](cPkgs.md) page.


---




## What is a Deployed Version? ##
_**Note: There is an alternate method of distributing Tunnelblick that allows configurations to be automatically installed when Tunnelblick is installed and updated from your web server but does not require rebranding and uses the standard, digitally-signed Tunnelblick application. See [Auto-Install Configurations](cAutoInstall.md) and [Updatable Configurations](cUpdatableConfigurations.md).**_

A deployed version of Tunnelblick is a customized version of `Tunnelblick.app` which can include everything necessary to install and run Tunnelblick and connect to one or more VPNs. In particular, it may include one or more OpenVPN configuration files, and, usually, certificate and key files for authentication. It can also include shell scripts and text that will appear in Tunnelblick's "about" window, and can specify user preferences that are forced to particular values and are read-only.

A Deployed version can specify additional commands and submenus to be added to the Tunnelblick menu, including specific programs to be run when a menu item is chosen. A Deployed version can also specify programs to be run at the end of the Tunnelblick launch process and/or before a connection is attempted. These features are described in [Additional Menu Commands and Programs](#Additional_Menu_Commands_and_Programs.md).

Note: By default, deployed versions of Tunnelblick display only the deployed configurations. They do not display private or shared configurations. To display shared or private configurations, set the "usePrivateConfigurationsWithDeployedOnes" or "useSharedConfigurationsWithDeployedOnes" preferences to yes. (See [Preferences](zPrefs.md)).

## How it Works ##
You create a deployed version of Tunnelblick by putting a "Deploy" folder into the `Contents/Resources` folder of `Tunnelblick.app`. `Deploy` can contain any one or a combination of configuration files, certificate and key files, up/down scripts, and a "forced-preferences.plist" file. Since `Deploy` and its contents can not be modified by a non-administrator user, this is a secure way to ensure that your users do not tamper with any settings that you wish to protect.

If `Contents/Resources/Deploy` exists, Tunnelblick's behavior changes:
  * If `Deploy` contains one or more .conf or .ovpn files, Tunnelblick uses it, instead of `~/Library/Application Support/Tunnelblick/Configurations`, for configuration files. When a connection is attempted, the log entry that Tunnelblick puts in the "VPN Details…" window will contain "from Deploy" if `Deploy` is being used for configuration files.

> Note: if configuration files are not in `Deploy`, their names may be changed by an unprivileged user. Any forced preferences for a configuration whose name has been changed will be ignored, because the forced preferences will be referring to the original configuration name.
  * If `Deploy` contains certificate and key files, those files can be referenced from configuration files by using the name of the file (i.e., no path need be given).
  * If `Deploy` contains up/down scripts with specific names (see [Up and Down Scripts](#Up_and_Down_Scripts.md)) and "Set nameserver" is selected, those scripts will automatically be used by Tunnelblick instead of the standard up/down scripts.
  * If `Deploy` contains a "forced-preferences.plist" file, Tunnelblick will use the preferences in it to override corresponding preferences in the user's `~/Library/Preferences/com.openvpn.tunnelblick.plist`. See [Forced Preferences](Forced_Preferences.md) for details. See[Preferences](Preferences.md) for a list of all preferences.
  * If `Deploy` contains a "Menu" folder, Tunnelblick will add entries in it to the Tunnelblick menu and/or use entries in it to run programs (see  [Additional Menu Commands and Programs](#Additional_Menu_Commands_and_Programs.md).
  * If `Deploy` contains an "IconSets" folder, Tunnelblick will search it for a set of images to use for animating the Tunnelbilck icon. See [Icon Animation](cIconAnimation.md).

Certificate and key files may usually be referenced within a configuration file without path information:
  * If `Deploy` contains _only_ `*.conf`, `*.ovpn`, `*.up.sh`, `*.down.sh`, and `forced-preferences.plist` files, the `~/Library/Application Support/Tunnelblick/Configurations` folder will be used as the target of the OpenVPN `--cd` option, which means that files in that folder may be specified in the configuration file without path information -- e.g., "key xxx.key".
  * If `Deploy` contains _any other files_ (for example, `*.key` files), then `Deploy` will be used as the target of the OpenVPN `--cd` option, which means that files in `Deploy` may be specified in the configuration file without path information -- e.g., "key xxx.key".

Each time Tunnelblick starts:
  1. If there is no `Contents/Resources/Deploy` folder and there is a backup folder for it, `Deploy` is restored from the backup without any user intervention. This happens when `Tunnelblick.app` is updated, either by the built-in update mechanism, or by reinstalling, upgrading, or downgrading Tunnelblick.
  1. If not already the owner, "root" is made the owner of everything in `Contents/Resources`, including `Deploy` and its contents, and of `Contents/Info.plist`
  1. If not already set, the permissions of `Contents/Info.plist` and of all items within `Contents/Resources` are set to "644" (root can read/write, everyone else can read), except
    * The permissions of `openvpnstart` are set to 4111 (setuid, anyone can execute)
    * The permissions of the standard up/down scripts, `installer`, `leasewatch`, and `openvpn` are set to 744
    * The permissions of the `*.executable` files are set to 755
    * The permissions of the following files in `Deploy` are given different permissions:
      * `*.cer`, `*.crt`, `*.der`, `*.key`, `*.p12`, `*.p7b`, `*.p7c`, `*.pem`, and `*.pfx` files are given permissions of "600" (root can read/write, nobody else can read)
      * `*.sh` files are given permissions of "744" (root can read/write/execute, everyone else can read)
  1. If any  ownerships or permissions were changed, or if `Deploy` has just been restored, a new backup of `Deploy` is made. The backup is owned by root and has the same permissions as the original items in `Deploy` (as modified in 3, above).

## Backups of `Deploy` ##
Backups of `Deploy` are created in `/Library/Application Support/Tunnelblick/Backup/A/B/C/D/E…/TunnelblickBackup`, where `/A/B/C/D/E…` is the absolute path to `Tunnelblick.app` itself. For example, if `Tunnelblick.app` is located in `/Applications`, the Deploy backup would be stored in `/Library/Application Support/Tunnelblick/Backup/Applications/TunnelblickBackup`. This allows each copy of Tunnelblick on a computer to have its own backup. Up to three backups are kept for each copy of Tunnelblick: the current and previous Deploy, and Deploy at the time Tunnelblick was first run from it's current location.

If `Tunnelblick.app` is moved, a new backup will be created for the new location the first time `Tunnelblick.app` is run in the new location. The old backup will continue to exist, however, this is not in itself a security risk because moving `Tunnelblick.app` (after it is first run and a backup of Deploy has been made) requires authorization by an administrator. It is suggested that any such move be followed by deletion of the backup, which also requires an administrator. Otherwise a fresh copy of Tunnelblick in the old position in the file hierarchy could be used to connect to the VPN because its `Deploy` folder would be "recovered" from the backup the first time it is run.

If `Tunnelblick.app` is renamed (which, depending on where it is stored, may not require an administrator's username/password), the backup mechanism still works normally. Note: Tunnelblick disables updates if the app has been renamed.

If two copies of `Tunnelblick.app` exist within the same folder in the filesystem hierarchy (with different names), they will use the same backup. This could lead to problems if one uses Deploy and the other doesn't, or if the contents of the `Deploy` folders are not identical. One way to have multiple Tunnelblicks in one folder without causing this problem is to locate the `Tunnelblick.app`s in different folders, but put aliases to each of them in the folder that is visible to the user. Multiple copies of `Tunnelblick.app` cannot be placed in the same folder without an administrator doing it, so this should not be a security risk.

## Signed vs. Unsigned Versions ##
A copy of Tunnelblick can be signed or unsigned. All non-Deployed versions of Tunnelblick should be signed versions, but signing interferes with some Deployed configurations. Use an unsigned version if users will be able to store usernames/passwords/passphrases in the Keychain and the Deploy folder is added after the Tunnelblick build process (which is where signing is usually done). See [Tunnelblick and Digital Signatures](cDigitalSignatures.md) for details.

## Additional Menu Commands and Programs ##
If the Deploy folder contains a "Menu" subfolder, it can contain items that will be added to the Tunnelblick menu (either as menu items or submenus) and programs that will be executed when Tunnelblick launches and before a connection is made.

The “Menu” folder can contain zero or more additional items to be inserted into the Tunnelblick menu, immediately above the “Quit Tunnelblick” item.

Each item in the Menu folder should be either a subfolder or an executable file with an .executable extension:

  * If it is a subfolder, a submenu will be created with the subfolder's contents. The name of the subfolder will be used as the name of the submenu.

  * If it is an executable file with extensions of “.runOnLaunch.executable", execution of the file will be started when Tunnelblick is launched, immediately before starting the processing of any “connect when Tunnelblick starts” configurations.

  * If it is an executable file with extensions of “.runOnLaunch.wait.executable", the file will be executed to completion when Tunnelblick is launched, immediately before processing any “connect when Tunnelblick starts” configurations. If the file returns a status non-zero status code, the launch of Tunnelblick will be abandoned before any “connect when Tunnelblick starts” configurations are connected..

  * If it is an executable file with extensions of “.runOnConnect.executable", execution of the file will be started when a connection attempt is made (either by the user or by a “connect when Tunnelblick launches” configurations, but not when a "connect when the computer starts" configuration).

  * If it is an executable file with extensions of “.runOnConnect.wait.executable", the file will be executed to completion when a connection attempt is made (either by the user or by a “connect when Tunnelblick launches” configurations, but not when a "connect when the computer starts" configuration). If the file returns a status non-zero status code, the connection attempt will be abandoned.

  * If it is an executable file with extensions of “.addToMenu.executable", a menu item will be created and the file will be executed when the user selects the menu item.

  * If it is an executable file with extensions of “.addToMenu.wait.executable", a menu item will be created and the file will be executed when the user selects the menu item. Tunnelblick will not respond to further user input until the file returns control. (Traffic over connections may stall under certain circumstances while waiting for the file to return control.)

  * If it is anything else, it will be ignored.

Note: An "executable" file may be any executable file. The .executable extension is required so that Tunnelblick will set permissions on the file to allow it to be executed by the user. The file will be owned by root, with permissions of 755.

The first “runOnLaunch” and “runOnConnect” files to be found will be the only ones processed. Care should be taken to name subfolders such that they are alphabetically after  these files; otherwise the subfolder(s) will be processed first, and any “runOnLaunch” and “runOnConnect” file in them will be processed first and be used when Tunnelblick is launched or a connection is attempted.

Items from the Menu folder (and any subfolders) will be listed on the menu in alphabetic order by filename.

Names (of files used as menu commands and folders used as submenu names) are modified for display to the user in the menu as follows:

  1. Any “.executable” extension will be removed.
  1. Any “.wait” extension from the result will be removed.
  1. If the result contains an underscore (“_”), everything up to and including the underscore will be removed.
  1. The result will be localized using Tunnelblick's Localizable.strings files.
  1. The result will be displayed to the user._

### Example ###

If /Contents/Resources/Deploy/Menu/ contains:<br>
<blockquote>000<i>.runOnConnect.wait.executable</i><br>
000<i>.runOnLaunch.wait.executable</i><br>
</blockquote><blockquote>001_First.addToMenu.executable<br>
002_Second.addToMenu.wait.executable<br>
003_Third.addToMenu.executable<br>
004_Fourth/<br>
<blockquote>Sub-1.addToMenu.executable<br>
Sub-2.addToMenu.executable<br>
</blockquote>005_Fifth.addToMenu.executable<br></blockquote>

The bottom of the Tunnelblick menu will look like this:<br>
<br>
<pre><code>	VPN Details…<br>
        --------<br>
	Options<br>
        --------<br>
	First<br>
	Second<br>
	Third<br>
	Fourth &gt;<br>
		Sub-1<br>
		Sub-2<br>
	Fifth<br>
        --------<br>
	Quit Tunnelblick<br>
</code></pre>
In this example, the prefixes <code>001_</code>, <code>002_</code>, etc. specify the order in which the items will be listed, but are removed (along with the extensions) before being displayed to the user.<br>
<br>
If the appropriate Localizable.strings file contains<br>
“First” = “XXXXX”<br>
“Second” = “YYYYY”<br>
<br>
Then the bottom of the Tunnelblick menu will look like this:<br>
<br>
<pre><code>	VPN Details…<br>
        --------<br>
	Options<br>
        --------<br>
	XXXXX<br>
	YYYYY<br>
	Third<br>
	Fourth &gt;<br>
		Sub-1<br>
		Sub-2<br>
	Fifth<br>
        --------<br>
	Quit Tunnelblick<br>
</code></pre>

In addition to the menu commands and submenu added, the file <code>000_.runOnLaunch.wait.executable</code> will be run at the end of the Tunnelblick launch process. Because ".wait" is specified, Tunnelblick will wait until the program finishes and examine the program's exit status. If the exit status is zero, Tunnelblick will finish launching, including making and "connect on launch" connections. If the exit status is non-zero, Tunnelblick will terminate immediately without any indication to the user other than an entry in the Console log. Before each connection attempt (either automatic or user-initiated), <code>000_.runOnConnect.wait.executable</code> will be run before the connection is made. (It will be called with the same arguments used to run the openvpnstart program.) Because ".wait" is specified, Tunnelblick will wait until the program finishes and examine the program's exit status. If the exit status is zero, Tunnelblick will attempt to make the connection. If the exit status is non-zero, the connection will be abandoned without any indication to the user other than an entry in the Console log.<br>
<br>
<h2>What about Updates?</h2>
A version of Tunnelblick with <code>Deploy</code> will work with Tunnelblick's standard update process, either through the the built-in update mechanism, or by reinstalling, upgrading, or downgrading Tunnelblick. An update replaces <code>Tunnelblick.app</code> with a new copy without <code>Deploy</code>; however, when the updated program is first run, <code>Deploy</code> will be restored from the backup copy, and will then be used normally. Note: "about.html" is not included in standard Tunnelblick updates, so it will be lost when there is a standard update because it is not located in <code>Deploy</code>.<br>
<br>
<h2>Forced Preferences</h2>
Preferences in <code>Deploy/forced-preferences.plist</code> override the user's normal preferences located in <code>~/Library/Preferences/com.openvpn.tunnelblick.plist</code>. Wildcards can be used to simplify the specification of forced preferences for multiple configurations.<br>
<br>
Forced preferences are implemented as follows:<br>
<ol><li>If a forced preference has the same name as a normal preference, the forced preference is used instead of the normal preference.<br>
</li><li>If a forced preference begins with an asterisk ("<code>*</code>") and the rest of the forced preference matches the end of a normal preference, it is used instead of the normal preference.<br>
</li><li>Otherwise the normal preference is used, or the default if there is no normal preference.</li></ol>

A forced preference consisting only of an asterisk ("<code>*</code>") will be ignored.<br>
<br>
For example, with forced preferences of <code>*useDNS</code>= TRUE and <code>config1useDNS</code> = FALSE, configuration <code>config1</code> will be forced to not use DNS, and all other configurations will be forced to use DNS. The user will not be able to change any <code>useDNS</code> preferences.<br>
<br>
Another example: forced preferences of <code>*ABCuseDNS</code>= TRUE, <code>*DEFuseDNS</code>= FALSE, configuration <code>configABC</code> will be forced to use DNS, and <code>configDEF</code> will be forced to not use DNS. The user will be able to change <code>useDNS</code> preferences for other configurations, if any.<br>
<br>
There are two <b>exceptions</b> to the way forced preferences work:<br>
<ul><li>All forced preferences with a key beginning with "SU" are ignored. These preferences are used privately by Sparkle Updater (which Tunnelblick uses to update itself), and should not be used. Tunnelblick provides preferences (which can be forced) which control the update process and override these Sparkle preferences.<br>
</li><li>Forcing the <i>config-name</i>-keychainHasPrivateKey and <i>config-name</i>-keychainHasUsernameAndPassword preferences -- regardless of value -- prevent the user from storing or using passphrases, usernames, or passwords for that configuration in the Keychain. Dialog boxes will not include a "Save to Keychain" checkbox, and any passphrases, usernames, and passwords in the Keychain will be ignored.</li></ul>

See<a href='Preferences.md'>Preferences</a> for a list of all preferences.<br>
<br>
<h2>Up and Down Scripts</h2>
If "Set nameserver" is selected, <code>Tunnelblick.app</code> starts OpenVPN with the "--up" and "--down" options specifying scripts to be run after the tunnel is established and before it is torn down. The standard scripts are <code>Contents/Resources/client.up.osx.sh</code> and <code>Contents/Resources/client.down.osx.sh</code> if "Monitor connection" is checked, and <code>Contents/Resources/client.nomonitor.up.osx.sh</code> and <code>Contents/Resources/client.nomonitor.down.osx.sh</code> if "Monitor connection" is not checked.<br>
<br>
However, if <code>Contents/Resources/Deploy/</code><i><code>config-name</code></i><code>.up.sh</code>, <i><code>config-name</code></i><code>.down.sh</code>, <i><code>config-name</code></i><code>.nomonitor.up.sh</code>, or <i><code>config-name</code></i><code>.nomonitor.down.sh</code> exist, each will be used instead of the corresponding standard script.<br>
<br>
<h2>What is Needed to Make a Deployed Version</h2>
To make a deployed version of Tunnelblick, you need whatever is required to connect to your VPN.<br>
<br>
To be more specific, you need:<br>
<ul><li>A copy of the Tunnelblick .dmg file with Tunnelblick version 3.0b22 or later. The latest version may be downloaded from <a href='http://code.google.com/p/tunnelblick'>the Tunnelblick website</a>.<br>
</li><li>Use an unsigned version of the Tunnelblick .dmg if your users will store usernames/passwords/passphrases in the OS X Keychain; otherwise you may use and signed version.<br>
</li><li>Optional: one or more OpenVPN configuration files, with extensions of ".ovpn" or ".conf".<br>
</li><li>Optional: certificate and key files for authentication.<br>
</li><li>Optional: shell script files, with extension ".sh", if you do not use Tunnelblick's "Set nameserver" feature. If you have shell files, they must have an extension of "sh"; otherwise they will not have execute permissions.<br>
</li><li>Optional: "about.html" file, containing text that will be displayed in Tunnelblick's "about" window.<br>
</li><li>Optional: "forced-preferences.plist" file, containing user preferences that you wish to override.<br>
</li><li>Optional: other files that you want your configuration file or scripts to be able to use.</li></ul>

<h2>How to Make a Deployed Version</h2>
<ol><li>Create a new folder on your Desktop and rename it "Deploy"<br>
</li><li>Copy any of the optional files you wish to use into the "Deploy" folder<br>
</li><li>Open the Tunnelblick .dmg file. A new Finder window will appear with (among other things) <code>Tunnelblick.app</code>
</li><li>Drag <code>Tunnelblick.app</code> to the Desktop (or some other place you will work with it). This is the copy you will modify to create your deployed version.<br>
</li><li>Right-click on <code>Tunnelblick.app</code>, and click "Show Package Contents". A new Finder window will appear with a folder "Contents".<br>
</li><li>Double-click on "Contents". The window will change to show several items. One of them is a folder, "Resources"<br>
</li><li>Option-drag your "Deploy" folder and drop it onto "Resources" to copy the folder into "Resources"<br>
</li><li>If you have one, copy your "about.html" file into "Resources"<br>
</li><li>Close the window that contains "Resources"</li></ol>

That's it! You are done! <code>Tunnelblick.app</code> has your new version of Tunnelblick with a <code>Deploy</code> folder containing everything that Tunnelblick needs for connection to your VPN.<br>
<br>
However, <b>DO NOT RUN THIS COPY</b>. Instead, make a copy of it and use the copy. When Tunnelblick is first run it makes changes to the ownership and permissions of parts of the application. That makes it inconvenient to copy, move, or modify the application after it has been run without entering administrator credentials, so keep a copy that has never been run.<br>
<br>
<h2>How to Use a Deployed Version</h2>
Using a deployed version of Tunnelblick is the same as using a non-deployed version, except:<br>
<ul><li>You will not be asked for administrator credentials the first time you first connect to a VPN. (Because ownership and permissions on the configuration file(s) was secured the first time the deployed version of Tunnelblick was run on the computer.)<br>
</li><li>Anyone with access to a deployed version of <code>Tunnelblick.app</code> can connect to its VPN(s). For example, if a deployed version of <code>Tunnelblick.app</code> is placed in /Applications, it can be accessed by any user of the computer, without requiring administrator credentials to set up secure configuration files in ~/Library/Application Support/Tunnelblick/Configurations -- because ~/Library/Application Support/Tunnelblick/Configurations is not used and the configuration files are shared by all users with access to the application.</li></ul>

<h2>Creating a .zip File for Deployment</h2>
To create a .zip file of your new version of Tunnelblick:<br>
<ol><li>Right-click on your new version of Tunnelblick, and click "Compress Tunnelblick.app"<br>
That's all. There is no step 2. Your .zip file has been created.</li></ol>

<h2>Creating a .dmg File for Deployment</h2>
<ol><li>Create a new folder on your Desktop and rename it "Tunnelblick"<br>
</li><li>Copy whatever you want to include in the .dmg file into the folder, including your new version of <code>Tunnelblick.app</code>
</li><li>Open <code>/Applications/Utilities/Disk Utility</code>
</li><li>Chose "File", then "New", then "Disk Image from Folder"<br>
</li><li>Select the folder you set up in steps 1. and 2. and click the "Image" button<br>
</li><li>Type a name for your .dmg file, and select a location in which to store it<br>
</li><li>Select "Image Format: compressed", and "Encryption: none"<br>
</li><li>Click "Save"<br>
Within a few moments, your .dmg file will be created.</li></ol>

<hr />

<h3>PLEASE USE THE <a href='https://groups.google.com/forum/#!forum/tunnelblick-discuss'>TUNNELBLICK DISCUSSION GROUP</a> FOR COMMENTS OR QUESTIONS