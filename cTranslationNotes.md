**Translation Notes**



  * This document has comments about some particular strings that are used in Tunnelblick.

  * For an overview of how Tunnelblick is localized, see [Tunnelblick Localization](cLocalizeTranslate.md).



&lt;hr&gt;



There is a series of "Window text" strings: **"B"**, **"KB"**, **"MB"**, **"GB"**, **"TB"**, **"PB"**, **"EB"**, and **"ZB"**. These are abbreviations for bytes, kilobytes, megabytes, gigabytes, terrabytes, petabytes, exabytes, and zetabytes, respectively.

There is a similar series of strings: **"B/s"**, **"KB/s"**, **"MB/s"**, etc., which refer to byes per second, kilobytes per second, megabytes per second, etc.

Several strings refer to the "**apparent public IP address**". That is the address that the computer presents when it requests something on the Internet (its return address, if you will). When a computer asks for a web page, for example, it tells the web server to reply to a public IP address. I use the word "apparent" because it isn't the IP address of the computer itself (which may be on a LAN and have a private IP address such as 192.168.0.123), but it is the IP address of the computer as far as the outside world is concerned.

Several strings refer to something as **"being forced."**. They refer to a setting that the user cannot change. "Deployed" versions of Tunnelblick can contain a "forced-preferences.plist" file that specifies the values of preferences that are usually chosen by the user. Any preference that appears in this file is "forced" to the value specified in the file, and the user is not allowed to change it.



&lt;hr&gt;



**" (?)" Window title** is used only if an internal error in Tunnelblick has made a string unavailable. (The user should never see it, but you never know…).

**"Check for a change" Button** is in response to a dialog window with a long message that starts
> "Tunnelblick can check that the apparent public IP address of your computer changes when you connect to a VPN, and warn you if it doesn't"
so it is talking about a checking for a change in IP address. (See "**apparent public IP address**" above.)

**"Common" Credentials group** is the name of a "credentials group" -- something new in Tunnelblick 3.3. A credentials group is a set of configurations that all share the same credentials (username and password). For example, most VPN service providers give a user one username and password, which works for all of the configurations (servers). If a user has not defined any credentials groups, there is one named "Common" that can be used. So "common" is used in the sense of having something "in common" or "shared".

**"Do not check for a change" Button** refers to the same dialog window as **"Check for a change"** (above).

**"(None available)" Button** will appear in the drop-down box to the right of "Icons:" in the Appearance tab. It indicates that there are no icon sets to choose from. This should never happen unless someone is creating a customized version of Tunnelblick or something has gone horribly wrong in the program. (We have to put something there.)

**"Only a Tunnelblick VPN Configuration (.tblk) can start when the computer starts." Window text** is displayed when a user tries to set a configuration to start when the computer starts, but the configuration is not a "Tunnelblick VPN Configuration" (.tblk). This should never happen in Tunnelblick 3.3 because all configurations must be .tblks, but if a non-.tblk configuration is somehow being shown (because of a bug), this message would appear.

**"Prepend domain name to search domains" Checkbox name** is the description for a checkbox. If checked, it means that the domain name (DNS name) of the computer will be prepended -- put a the front of -- the list of search domains. "Search Domains" is the label on the bottom row on the right of the Network System Preference (in English), underneath "DNS Server:".

**"This 'Deployed' version of Tunnelblick cannot be  launched or installed because it has not been rebranded**<font color='grey'> <i>(rest of string omitted)</i></font>" Window text**-- here "rebranded" means renamed, with all references to the name "Tunnelblick" replaced by something else.**

**"Latest (%@)"** Button -- this refers to the latest (newest) version of OpenVPN and is used in the list of OpenVPN versions that the user can choose to use. It is like the "Default (%@)" button.

**"LANGUAGE\_LOCALIZATION"** -- This is a description of localization for your language. For example, for the German translation, it is "Deutsche Lokalisierung".

**"LEAD\_TRANSLATORS"** -- This should be "translated" into a list of the names of the main translators (lead translators). These names will be listed in the top section of the credits on the "Info" panel. All translators, including those in this list, will be included in the localization section -- the third section -- of the credits. For example, for the German translation, it is "Markus Schneider, Andreas Finke und Janek Schwar".



---

### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS