**Translating .strings Files**

This document gives an overview of the _old_ way to localize Tunnelblick, editing .strings files.

For a description of the _new_ way to localize Tunnelblick, see [Localizing Tunnelblick](cLocalizeTranslate.md).

For notes about specific strings that are being translated, see [Translation Notes](cTranslationNotes.md).



&lt;hr&gt;







&lt;hr&gt;



## .strings Files ##
Tunnelblick has two .strings  files for each language:
  * A "Localizable.strings" file, which contains all of the strings used by Tunnelblick, whether they have been translated or not (and an indication of those that have not been translated); and
  * A "NeedsTranslations.strings" file, which contains only the strings that have not yet been translated. (If there are no strings to be translated, this file may not exist.)

There may also be a "Removed.strings" file, which contains strings that were used in an old version of Tunnelblick but are no longer being used. They may contain useful translations.

If you are the first translator for a language, you will be editing a Localizable.strings file. If you are working on a language that has been worked on before, you could be editing either a NeedsTranslation.strings file or a Localizable.strings file -- it is your choice. But only edit one file, not both.

## Editing .strings Files ##
If you have Xcode, you can just double-click the files to open them in Xcode, which works fine.

<font color='red'>You can edit .strings files in <code>TextEdit</code>, but you need to open them a special way.</font>**If you double-click them, or just File | Open them, things might look OK, but they aren't. The .strings files are in a special format called UTF-8, and need to be opened, edited, and saved in that format or bad things happen (such as losing diacritical marks or changing characters into different characters!)**

To open one of the .strings files in `TextEdit`:
  1. Open `TextEdit`, which is in /Applications
  1. Click "File", then "Open"
  1. Navigate to and select the .strings file you wish to edit
  1. At the bottom of the window to the right of "Plain Text Encoding", select "Unicode (UTF-8)
  1. At the bottom of the window, remove the check in the "Ignore rich text commands" checkbox if there is one
  1. Click the "Open" button

Now you can edit the file. When you are done, be sure to save it. If you do a "Save As", be sure to save it as "Unicode (UTF-8)".

## Doing the Translations ##
The .strings files all have the same format. They contain a series of lines that look like this:

```
/* Button */
"Disconnect" = "Desconectar";
```
The first line, /`*` Button `*`/, is a hint about what the string is used for -- this one tells you that the string "Disconnect" is for a button. Other hints may indicate a string is for the title of a window, or the text of a window, or is a status  message from OpenVPN.

The second line has two strings, separated by an equal sign and followed by a semicolon. The first string is in the language that the application was developed in (English), and the second string is in the "target" language.

In the example above, from the "ES.lproj" folder (Spanish), "Disconnect" is the English string, and "Desconectar" is the equivalent in Spanish.

Here are some lines from a NeedsTranslation.strings file:

```
/`*` Connection status `*`/
"AUTH" = "Authorizing";

/`*` Window title `*`/
"Authentication failed" = "Authentication failed";

/`*` Checkbox name `*`/
"Automatically connect on launch" = "Automatically connect on launch";

/`*` Button `*`/
"Cancel" = "Cancel";
```

Notice that both of the strings on each line are in English (sort of). The string "AUTH" is a string describing a connection's status -- what it is doing -- in this case, the status is something called "AUTH". The second string is the string as it should be displayed to the user -- this is what you as translator are to replace. Note that for the last three examples, both strings are identical in English. That is more common. The program requests that the title of a window be "Authentication failed", for example, and, in English, that should be displayed as "Authentication failed".

Translation consists of replacing the second string on each line with the target language's equivalent, using the hint on the line above the strings. **Please do not modify anything in the file outside of the second string.**

"Localizable.strings" will have a "/`*` Needs Translation `*`/" comment before every line that appears to not have been translated. (A program we use to create these files decides that a line needs translating if the left-side and right-side strings are identical, which does not always mean they need translation, but is a reasonable guess.) You can (but do not need to) remove the "/`*` Needs Translation `*`/" comments on any strings that you have translated. If appropriate, it will be removed automatically when the .strings file is integrated into Tunnelblick.

## If a String is the Same in Both Languages ##
If a string is the same in both English and the target language, then put a hint of
> `/* TRANSLATION SAME AS DEVELOPMENT */`
before the string. For example,
```
/* TRANSLATION SAME AS DEVELOPMENT */ /* Button */
"OK" = "OK";
```
This helps the program which process the strings files understand that the string does not need translation.

## Weird Characters in the Strings ##
Some of the strings have character sequences of "\n". This causes a line break when the text is displayed. A sequence of "\n\n" would cause a line break followed by an empty line.

Some of the strings have %@, %d, or other special sequences of characters. They indicate a place where some other item (a filename, a number, etc.) will be inserted into the string. Usually that's all there is to it. However, when there are two or more such items in one string, the target language may need to use them in a different order than English uses.

Here's an example: for English speakers, one of the distinctive features of the character Yoda in _Star Wars_ was the way he spoke -- he spoke "backwards". For example, he would say "Hot the food is", when the usual way to express that in English is "The food is hot". If the line in Localizable.strings was
```
"The %@ is %@" = "The %1$@ is %2$@";
```
we would translate that into Yoda's English by changing it to
```
"The %@ is %@" = "%2$@ the %1$@ is"
```
(We'll ignore the fact that %2$@ needs to be capitalized because it now starts a sentence.)


---

### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS