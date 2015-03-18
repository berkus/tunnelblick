**Localizing Tunnelblick**



&lt;hr&gt;



This document gives an overview of the _old_ way to localize Tunnelblick.

For an overview of the _new_ way to localize Tunnelblick, see [Localizing Tunnelblick](cLocalizeTranslate.md).

For instructions on editing the .strings files, see [Translating .strings Files](cTranslateStrings.md).

For notes about specific strings that are being translated, see [Translation Notes](cTranslationNotes.md).



&lt;hr&gt;



## How Localization Work in Tunnelblick ##
Although some applications have elaborate structures to specify translations, Tunnelblick's is simple:
  * Inside of Tunnelblick.app there is a folder for English and a folder for each language that has been translated.
  * Each of these folders contains a "Localizable.strings" file for the language. That file is used "on-the-fly" to translate the Tunnelblick application's strings, which are in English, to the language specified in the user's System Preferences.

Most language folders have as a name the [ISO-639-1](http://www.loc.gov/standards/iso639-2/php/code_list.php) two-letter abbreviation of the language and an extension of "lproj". For example, "JA.lproj" is the folder with Japanese strings, "ES.lproj" is the folder with Spanish strings, etc. One exception is English, which is named English.lproj. That is because Tunnelblick's original development language was English. Other exceptions include "ZH\_CN.lproj" for simplified Chinese and "ZH\_TW.lproj" for traditional Chinese.

NOTE: Prior to Tunnelblick versions 3.0b24, all .lproj folders had the English name of the language, instead of the ISO-639-1 two-letter abbreviation of the language.

## Adding Your Translations to Your Copy of Tunnelblick ##
**If you made the first translation of a language**, here's how to put your modified Localizable.strings file into your copy of Tunnelblick:
  1. Look up the ISO 639-1 two-character abbreviation for the language. You can do that at http://www.loc.gov/standards/iso639-2/php/code_list.php
  1. Create a folder on your Desktop named with the two-character abbreviation followed by ".lproj" (e.g., "CA.lproj" for Catalan/Valencian)
  1. Put the Localizable.strings file that you have modified in the folder
  1. Get a fresh copy of Tunnelblick (one that has never been used; copy from a downloaded disk image file if necessary) and put it on your Desktop
  1. Right-click on the Desktop "Tunnelblick.app" and click on "Show Package Contents". A new Finder window will appear
  1. Double-click on "Contents" in the new window. The window should now show several items
  1. Drag the folder you created in step 2, above, and drop it on "Resources"
  1. Close the Finder window

You're done. The copy of Tunnelblick.app on your Desktop now has your translations.

<font color='red'>Note: This process invalidates Tunnelblick's "digital signature", and you will be warned about it being a modified version of Tunnelblick.</font> If you have added translations, you are encouraged to submit them to be included in Tunnelblick; contact project owner Jon via email at jkbullard at gmail dot com.

**If you edited an existing translation**, here's how to put your modified .strings file into your copy of Tunnelblick:
  1. Put the Localizable.strings file that you have modified in the folder
  1. Get a fresh copy of Tunnelblick (one that has never been used; copy from a downloaded disk image file if necessary) and put it on your Desktop
  1. Right-click on the Desktop "Tunnelblick.app" and click on "Show Package Contents". A new Finder window will appear
  1. Double-click on "Contents" in the new window. The window should now show several items
  1. Double-click on "Resources". The window will now show several (different) items.
  1. Double-click on the .lproj folder of the language you have translated
  1. Drag the Localizable.strings file you have modified into the window. Tell Finder to replace the existing Localizable.strings file when you are asked
  1. Close the Finder window

You're done. The copy of Tunnelblick.app on your Desktop now has your translations.

<font color='red'>Note: This process invalidates Tunnelblick's "digital signature", and you will be warned about it being a modified version of Tunnelblick.</font> If you have added translations, you are encouraged to submit them to be included in Tunnelblick; contact project owner Jon via email at jkbullard at gmail dot com.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS