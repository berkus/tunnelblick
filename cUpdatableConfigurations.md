

## Updatable Configurations ##
A Tunnelblick VPN Configuration ("Configuration") can be updated the same way that the Tunnelblick application itself is updated. Because a Configuration can contain any number of Configurations within it, you can have a single Configuration that updates all of your VPN configurations at once.

Combined with [automatic installation](cPkgs#Automatic_Installation.md), this allows you to distribute Tunnelblick to your users with configurations that are updated separately from the program. You do not need to rebrand Tunnelblick, or build it from source -- you can use the standard Tunnelblick application.

By adding a few entries to a a Configuration's Info.plist file, a Configuration will become "updatable". When launched, and periodically afterward, Tunnelblick will check a webpage for information about updates to the configuration. If a new version of the Configuration is available, the user will be asked for permission to update it. If granted, the new configuration will be installed and available for use immediately, without relaunching Tunnelblick.

Configuration updates are handled by [Sparkle Updater](http://sparkle-project.org), just like Tunnelblick updates. (Sparkle is built into Tunnelblick.)

In addition to the Configuration itself, you must provide an update server -- a web server with the update information.

## What Makes a Configuration Updatable ##
To be updatable, a Configuration must contain an [Info.plist](cPkgs#Info.plist.md), and the Info.plist must include the following entries:
  * **CFBundleIdentifier**, a string containng a reverse-domain uniquely identifying the Configuration. For example, "com.example.tunnelblick.updatable-configurations.001".
  * **CFBundleVersion**, a string containing a version number consisting only of the digits 0-9 and periods. For example, "1.0", "1.3.1", etc.
  * **TBPackageVersion**, a string "1". (This is required in any Configuration Info.plist, whether or not it is updatable.)
  * **SUFeedURL**, a string with the URL for the "appcast" that gives information about updates to the Configuration. For example, "https`:``/``/`example.com`/`tunnelblick`/`configs`/`001`/`appcast`.`rss". If this is not an "https:" URL, the SUPublicDSAKeyFile entry and associated file are required.

Optional Info.plist entries include those normally allowed in the Info.plist of a Configuration -- **TBReplaceIdentical**, **TBSharePackage**, etc.

There is one optional Info.plist entry that is used only for updatable configurations: **TBKeepExistingFilesList**. This allows an update to omit files such as per-user key files that are different for each user and which already exists in the original Configuration that is installed on user's computer. This should be an array of filenames. Each filename is the name of a file that exists in the original Configuration (the one being replaced with an updated version) and that should be kept as it is and not updated. (Note: the updated file should not be included in the updated version.) Each "filename" may include a single asterisk ("`*`") character, which will match any number (including zero) of any character in a filename. For example:
  * **`*`** matches any filename
  * **abc`*`** matches any filename which starts with abc (e.g. "abc", "abcd", "abc.def.ghi.key", etc.)
  * **abc`*`def.key** matches any filename that starts with "abc" and ends with "def.key" (e.g. "abcdef.key", "abc.user12345.private.def.key", etc.
The other optional Info.plist entries for an updatable Configuration are all [Sparkle Updater](http://sparkle-project.org) entries. (Please note that Tunnelblick uses a customized version of Sparkle 1.5b6 so some features in newer versions of Sparkle may not be available.) Here are comments on some entries:
  * **SUScheduledCheckInterval**: The time, in seconds, between checks. Minimum of 60; default is 3600 (one hour).
  * **SUPublicDSAKeyFile**: The filename and extension of a file containing the public DSA key. This key and file are required if https: is not used in the SUFeedURL entry. The file must be contained in the Configuration, either directly in the .tblk, or in the .tblk/Contents/Resources folder.
  * **SUAllowsAutomaticUpdates**: If present, must be a binary "NO".
  * **SUEnableAutomaticChecks**: If present, must be a binary "NO".
  * **SUEnableSystemProfiling**: If present, must be a binary "NO".
  * **SUShowReleaseNotes**: If present, must be a binary "YES".
(Some of these "must be" restrictions may be relaxed in a later version of Tunnelblick.)

## Nested Configurations ##
An updatable configuration should be constructed using "nested" configurations, that is, as VPN configurations inside the updatable configuration. A typical updatable configuration might have a structure like this:
  * _Name for the updatable configuration_.tblk
    * Info.plist
    * dsa\_pub.pem _(recommended; not required)_
    * _Name for VPN configuration #1_.tblk
      * Info.plist
      * _This name is ignored_.ovpn _-- the OpenVPN configuration file for VPN configuration #1_
      * client.crt
      * client.key
      * _(other files such as CA certificates, scripts, etc.)_
    * _Name for VPN configuration #2_.tblk
      * Info.plist
      * _This name is ignored, too_.ovpn _-- the OpenVPN configuration file for VPN configuration #2_
      * client.crt
      * client.key
      * _(other files such as CA certificates, scripts, etc.)_

The Info.plist of the nested configurations must include a CFBundleIdentifier which is distinct from the CFBundleIdentifier for the outer configuration, and must also include a CFBundleVersion entry, along with a TBPackageVersion entry.

## The Update Server ##
The update mechanism uses a web server to provide update information. Minimally, that web server serves the following files:
  * The appcast: An XML file which contains information about available updates.
  * For each available update:
    * The release notes: An html page which is displayed to the user when the update is available.
    * The updated configuration: A .zip or .dmg file of the updated Configuration, suitable for downloading.

## The Appcast ##
The appcast is an XML file that contains information about each available update, including:
  * The conditions under which the update is considered appropriate.
  * The URL for the "release notes" page.
  * The URL for the updated configuration.

Here is a sample appcast.rss:
```
<rss version="2.0" xmlns:sparkle="http://www.andymatuschak.org/xml-namespaces/sparkle"  xmlns:dc="http://purl.org/dc/elements/1.1/">
	<channel>
		<title>Configuration appcast</title>
		<link>https://www.example.com/tunnelblick/configurations/001/appcast.rss</link>
		<description>Most recent changes with links to updates.</description>
		<language>en</language>
		<item>
			<title>Latest VPN Configurations (Recommended for all users)</title>
			<sparkle:releaseNotesLink>
				https://www.example.com/tunnelblick/configurations/001/UpdateNotes.html
			</sparkle:releaseNotesLink>
			<pubDate>Mon,  14 Jul 2014 14:55:20 -0400</pubDate>
			<enclosure
				url="https://www.example.com/tunnelblick/configurations/001/configurations.zip"
				sparkle:version="1.2.3"
				sparkle:shortVersionString="VPN Configurations 1.2.3"
				sparkle:dsaSignature="MCwCFE6twQrvEOeFyXLMCJsClV2tM7RGAhQ53VjexE4Gf0SSswNUSMkg3UeXZg=="
				type="application/octet-stream"
			/>
		</item>
	</channel>
</rss>
```

Notes on the appcast entries:

**_`<`title`>`_** and **_`<`description`>`_**

> The title and description entries are not shown to the user during the update process; they appear if you go to the page in an .rss browser.

**_`<`link`>`https`:``/``/`www.example.com`/`tunnelblick`/`configurations`/`001`/`appcast`.`rss`<`/link`>`_**

> The URL of the appcast.rss itself.

**_https`:``/``/`www.example.com`/`tunnelblick`/`configurations`/`001`/`UpdateNotes`.`html_**

> The URL of the page that is presented to the user to explain the update.

**_`<`pubDate`>`Mon,  14 Jul 2014 14:55:20 -0400`<``/`pubDate`>`_**

> The date that the update was published.

**_url="https`:``/``/`www.example.com`/`tunnelblick`/`configurations`/`001`/`configurations`.`zip"_**

> The URL of the update itself -- a .zip or .dmg file that contains the updated .tblk.

**_sparkle:version="1.2.3"_**

> The machine-readable version number of the update. Consists of one, two, or three numbers separated by periods. This is compared to the CFBundleIdentifier in the user's configuration to determine if the update is newer or not. _This should be the same as the CFBundleVersion in the Info.plist in the updated Configuration in the .zip or .dmg file._

**_sparkle:shortVersionString="VPN Configurations 1.2.3"_**

> The human-readable version number. This is what is presented to the user.

**_sparkle:dsaSignature="MCwCFE6twQrvEOeFyXLMCJsClV2tM7RGAhQ53VjexE4Gf0SSswNUSMkg3UeXZg=="_**

> The DSA signature of the update file. (The signature of the .zip or .dmg file.)

## Update Notes ##
The update notes are just an HTML file that is presented to the user when an update is available.

Here is the sample update notes file for Tunnelblick release 3.4beta30:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
  <head>
    <meta http-equiv="Content-type" content="text/html;charset=UTF-8">
    <title>Update Notes - Tunnelblick version 3.4beta30</title>
  </head>
  <body>
	    <table><tr>
	      <td width="90%" valign="middle"><big><strong>Tunnelblick 3.4beta30</strong></big></td>
	      <td align="right" valign="middle">
  	        <a href="https://code.google.com/p/tunnelblick/wiki/Donate">
              <img style="padding-top:6px;" src="https://tunnelblick.net/donate_button.gif" alt="Donate">
            </a></td>
	    </tr></table>




	  <strong>Changes since 3.4beta28:</strong>
        <ul>
	      <li><strong>Includes major enhancements to installing configurations.</strong></li>
	      <li><strong>Includes LZO version 2.08.</strong></li>
	      <li><strong>Changes many warning dialogs so they do not block other Tunnelblick operations.</strong></li>
	      <li><strong>Fixes several problems.</strong></li>
	    </ul>



Details are in the <a href="https://code.google.com/p/tunnelblick/wiki/RlsNotes">Release Notes</a><br><br>


    <hr>
	<span style="color:red"><strong>Please Note:</strong></span>
	<ul>
	  <li><strong>Disconnect all configurations before updating.</strong></li>
	  <li><strong>You will not be able to use Tunnelblick after updating without providing
	  a computer administrator's username and password twice: once to remove the old version, and
	  once to secure the new version.</strong></li>
	</ul>
  </body>
</html>
```

## https: and Digital Signatures ##
It is advisable to use https: for all update transactions.

If the updates are not done using https:, you must digitally sign the update.

Although using https: makes it unnecessary to digitally sign the update, signing is also recommended.

For more information on digitally signing the update, see the [Sparkle Updater](http://sparkle-project.org) documentation. (Note that (A) the digital signature is computed from the .zip or .dmg file, not the .tblk., and (B) the digital signature has nothing to do with the digital signature that applications on OS X use.)

## Debugging Configuration Updates ##
Debugging updates is difficult partly because there are so many parts to the update and partly because Sparkle's error messages don't usually say what is wrong. Here are some hints:

  * First, make sure that your initial configuration installs correctly by double-clicking it, then make sure that your updated configuration installs properly by double-clicking it. Because the update process simulates a double-click on the update, these installs must work before updates will work. Making sure that the initial and update configurations work as configurations themselves, before trying to use them as updatable configurations will help isolate problems.

  * Copy/paste the following command into Terminal to set a Tunnelblick preference which will add debugging info to the Console log:
> > _defaults write net.tunnelblick.tunnelblick DB-UC -bool yes_

> To remove the preference, copy/paste:
> > _defaults delete net.tunnelblick.tunnelblick DB-UC_

> The debugging information includes a lot of entries that are about the internal procedures that Tunnelblick uses to implement updatable configurations; most of these can be ignored.

  * Use the "Check Now" button on the "Preferences" panel of the "VPN Details…" window to test for updates. Although Tunnelblick will check for updates when it is launched, when doing that update check Sparkle will ignore errors and not complain about them. If you do a "Check Now" check, you will get either a window saying the item is up-to-date, an offer of an update, or an indication that an error occurred. Note: "Check Now" will first do a check for updates to the Tunnelblick application, and after you click "OK" to acknowledge that you have received that, it will check for configuration updates.

  * After you have installed a Configuration which is updatable, there should be a folder in /Library/Application Support/Tunnelblick/Tblks named "xxx.yyy.zzz\_nn", where "xxx.yyy.zzz" is the CFBundleIdentifier for the updatable .tblk and "nnn" is a number. That folder contains a "stub" .tblk whcin contains only a Contents folder which contains a copy of the Info.plist for the updatable .tblk, and (if a DSA signature file was specified with **SUPublicDSAKeyFile**), a "Resources" folder with the DSA signature file. If the xxx.yyy.zzz.tblk\_nnn is not present, Tunnelblick did not recognize that the configuration was updatable.

  * A Console log entry like "DB-UC: Copied updatable configuration 'com.example.config.001.tblk' to local user folder" should appear when Tunnelblick launches. (It means the corresponding folder in /Library/Application Support/Tunnelblick/Tblks was found.)

  * A Console log entry like "DB-UC: Delaying start of update check for configuration set com.example.config.001 may appear when Tunnelblick launches. It is normal -- update checks for configurations are delayed until after the update check for the Tunnelblick application.

  * A Console log entry like "DB-UC: Starting update check without UI for configuration 'com.example.config.001'; URL = https://example.com/config.001/appcast.rss" should appear when Tunnelblick launches. It indicates the start of a silent update check ("without UI" means "without user interface").

  * A Console log entry like "DB-UC: cfgUpdater 0x8a377b0: didFinishLoadingAppcast" means that Sparkle successfully found and downloaded the appcast for a configuration from the website. If no error messages from Sparkle appear following this, it means that the version number in the appcast was not higher than the version number in the Configuration that is installed (i.e., the version number in the Info.plist in /Library/Application Support/Tunnelblick/Tblks/xxx.yyy.zzz.tblk).

## More Information ##
For more information about the update process or these files, see the [Sparkle Updater website](http://sparkle-project.org). (Please note that Tunnelblick uses a customized version of Sparkle 1.5b6 so some features in newer versions of Sparkle may not be available.)


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS