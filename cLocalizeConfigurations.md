### Other Localization ###

As of build 4039, configurations, welcome windows, and added menu commands may be localized.





&lt;hr&gt;



## Localizing Configuration and Folder Names ##

Configuration names and the names of the folders that contain configurations can be localized.

A configuration can include localization information for itself. In a Deployed version of Tunnelblick,  localization information may be contained in the Deploy folder and used for all configurations.

For a configuration to include localization information itself, the configuration must include an [Info.plist](cPkgs#Info.plist.md) file and one or more "lproj" folders.



&lt;hr&gt;


**Info.plist**

The Info.plist file may contain any of the entries normally allowed in a [.tblk Info.plist](cPkgs#Info.plist.md), but for localization the file must include the following entries (each value is a string):
  * CFBundleDevelopmentRegion, "English"
  * CFBundleInfoDictionaryVersion, "6.0"
  * CFBundleIdentifier, a reverse-domain identifier which must be unique for each configuration, for example, "com.example.tunnelblick.configuration.001"



&lt;hr&gt;


**".lproj" folders"**

Each "lproj" folder (except English) has as its name the [ISO-639-1](http://www.loc.gov/standards/iso639-2/php/code_list.php) two-letter abbreviation of the language and an extension of "lproj". For example, "JA.lproj" is the folder with Japanese strings, "ES.lproj" is the folder with Spanish strings, etc. One exception is English, which is named English.lproj. Other exceptions include Chinese and other languages for which there are multiple dilalects. See [Localizing Resources](http://commons.oreilly.com/wiki/index.php/Learning_Cocoa_with_Objective-C/Miscellaneous_Topics/Localization#Localizing_Resources) or examine the "lproj" folders in /Applications/Tunnelblick.app/Contents/Resources.

Each "lproj" folder should contain a single file named "Localizable.strings".

Each "Localizable.strings" file should be a UTF-8 encoded text file with lines of the following format:

> "file or folder name"="translated name";

For example, if you have configurations in folders named "fast" and "slow", and each folder contains a "New York" and "San Juan" configuration, you would have a Localizable.strings file in each "lproj" folder. The file for English (in English.lproj) might look like the following:

> "fast"="fast";<br>
<blockquote>"slow"="slow";<br>
"New York"="New York";<br>
"San Juan"="San Juan";<br></blockquote>

The file for Spanish (in ES.lproj) might look like the following (Spanish speakers, please forgive any language errors!):<br>
<br>
<blockquote>"fast"="rápido";<br>
"slow"="lenta";<br>
"New York"="Nueva York";<br>
"San Juan"="San Juan";<br></blockquote>

You can download a <a href='http://sourceforge.net/projects/tunnelblick/files/All%20files/Misc/LocalizationWithSubfolderExample.tblk.zip/download'>sample of a "nested" .tblk</a> which contains a regular configuration and a configuration in a subfolder. The sample configurations are localized for English, German, and Spanish as described above.<br>
<br>
<br>
<br>
<hr><br>
<br>
<br>
<h2>Localizing a Deployed Version</h2>

Deployed versions of Tunnelblick may also be localized. That can be done with per-configuration localization as described above, or with a single folder for each language containing translations for all configurations, folders, and added menu items. Programs launched by added menu items are sent the current language as an argument, so even simple scripts can be localized.<br>
<br>
To localize configuration and folder names and the names of added menu commands, the Deploy folder must contain an OS X bundle (a folder with a special structure) named "Localization.bundle". That bundle must include a Contents folder, which must contain an Info.plist file with the three entries described above (no other entries are needed) and a "Resources" folder, which must contain one or more "lproj" folders. The "lproj" folders are as described above.<br>
<br>
To localize the names of added menu commands, include them in the "Localized.bundle" described above without any extensions (e.g., "foo", not "foo.addTo.Menu.executable"). Programs launched by added menu commands will be launched with the a lower-case version of user's current language as the first argument -- for example, "english", "cs", "zh_cn". Programs launched at Tunnelblick launch will also have the language as the first argument, but programs launched upon connection will only have the language as the first argument if the "Localized.bundle" exists (so as to not break existing setups, which might expect other arguments).<br>
<br>
The "Welcome Window" can also be localized. The "Welcome.bundle" is similar to the "Localized.bundle". It consists of a "Contents" folder which contains an Info.plist file with the three entries described above (no other entries are needed) and a "Resources" folder. The "Resources" folder should contain one or more "lproj" folders with names as described above. However, the contents of each "lproj" folder should be an "index.html" file which contains the "Welcome" page for a particular language (and any other files such as images that "index.html" refers to).<br>
<br>
Note: If a Deploy folder and an individual configuration contain conflicting localizations, the individual configuration's localization will be used.<br>
<br>
<hr />

<h3>PLEASE USE THE <a href='https://groups.google.com/forum/#!forum/tunnelblick-discuss'>TUNNELBLICK DISCUSSION GROUP</a> FOR COMMENTS OR QUESTIONS