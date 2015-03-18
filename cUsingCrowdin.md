**Using Crowdin for Tunnelblick Translations**





&lt;hr&gt;



## Signing Up to Translate for Tunnelblick ##

_Note: Tunnelblick translation is a_"private"_project on Crowdin, which means you need permission to join the project as a translator._

To use Crowdin to help translate Tunnelblick, you need:
  * A Crowdin account; and
  * Permission to translate one or more languages for Tunnelblick.

**If you don't have a Crowdin account**, please register at [Crowdin.com](https://www.crowdin.com). Registration is fast and free.

**Once you have a Crowdin account**, please email project owner Jon at his Gmail address, jkbullard. Please include:
  * The language you would like to help translate and any special qualifications you have (native speaker, lived there for four years, etc.);
  * Your Crowdin userid;
  * Your preferred email address;
  * The name you would like shown on Tunnelblick's [Thanks](cThanks.md) page and in the credits on Tunnelblick's "Info" panel; and
  * (Optional): Your real name.

When your email has been processed, Crowdin will send you an email "inviting" you to help translate Tunnelblick. Click on the link in the email and you will be authorized to translate.



&lt;hr&gt;



## Working with Crowdin ##
Working with Crowdin is self-explanatory for the most part. Here a a few things to keep in mind about the way Tunnelblick is using Crowdin:

  * When working on Crowdin, it is tempting to click the copy source button, translate the string, and then click the double arrow button next to it to move to the next one. However, **clicking the double arrow button loses your translation** when it moves you to the next string to translate. Instead, **click the commit button** when you want to save your translation. That will also move you to the next string to translate. (Thanks to Jarmo Isotalo for this tip!)

  * If you have a better translation for a string that has an "approved" translation (a translation with a green check mark -- most strings have them), please create a Crowdin "Comment" and make the comment a Crowdin "Issue". Otherwise your translation will be ignored.

  * When you write or reply to a Crowdin "comment" or "issue", if you include "@name" (where "name" is someone's Crowdin name) somewhere in your text, that person will get an email notifying them of the comment/issue.

  * For each string, the "approved" translation will be used. If there is no "approved" translation, the translation with the most votes will be used and will be "approved" in the next build.

  * Please notify an administrator if you propose a new translation for a string that already has an "approved" translation (indicated by a green check mark).

  * Crowdin can be set up to require that a "proofreader" approve all new translations, to ensure that translations are appropriate, but that means a lot more work for translators or proofreaders, so currently that feature is disabled. That may be changed in the future.

  * Weekly builds of Tunnelblick will be created so translators can see their progress, but the schedule will be adjusted as needed and they can be made "on demand" if necessary. To request a build with updated translations, email project owner Jon at jkbullard at gmail.



&lt;hr&gt;



## Questions or Comments ##

**If you have a question or comment that is not about a particular string**, please email to Gmail address jkbullard.

**If you have a question or comment about a particular string:**

Developers would like to be notified about questions or comments, so they can add "Context" or screenshots.
  1. Click "Request context" just below the English version of the string at the top of the middle column of the editing window;
  1. Type in a short note in English describing the problem or question; and
  1. Click "Submit".
The "short note" could be something like "What does the %@ refer to?" or "The English version of the string could be improved by…".

That will
  * Create a Crowdin "Comment" for the string, which will be shown to all translators for all languages, and
  * Make the comment an "Unresolved issue".
**Doing it this way is important**, because making the comment a Crowdin "Unresolved Issue" will cause developers to be notified about it by email. Developers are not notified about "Comments" that are not "Issues", so such comments may never be responded to.

A developer should respond by answering your question or comment. When doing that, the developer may add a screenshot or add "Context", perhaps from other translator's comments. Then:
  * If the developer thinks your question or comment has been fully responded to, the developer will mark the "Issue" as "Resolved".
  * If there is something that needs to be done, it will be left as an "Unresolved Issue".
Or maybe other translators (for any language) will respond; you or any translator may mark it as "Resolved".

When anyone marks the "Issue" as "Resolved", you will be notified by email, so you can check that your question or comment was dealt with to your satisfaction. If it wasn't, create a new "Issue" by clicking on "Request context" again. (An issue marked "Resolved" cannot be changed back to "Unresolved.)

Developers will occasionally look through all the "Comments", whether or not they are "Issues", and whether or not the "Issues" are resolved:
  * Useful comments may be copied (perhaps after editing) into the "Context";
  * Comments may be deleted (to reduce clutter); and
  * An "Unresolved Issue" may be marked "Resolved".



&lt;hr&gt;



## "Odd" characters in Strings ##
  * Some of the strings have character sequences of "\n". This causes a line break when the text is displayed. A sequence of "\n\n" would cause a line break followed by an empty line.

  * Some of the strings have %@, %d, or other special sequences of characters. They indicate a place where some other item (a filename, a number, etc.) will be inserted into the string:
    * %d, %u, %ld, %lu will all be replaced by a number.
    * %@ will usually be replaced by text such as the name of a configuration.
    * When there are two or more such items in one string, the target language may need to use them in a different order than English uses.

> Here's an example: for English speakers, one of the distinctive features of the character Yoda in _Star Wars_ was the way he spoke -- he spoke "backwards". For example, he would say "Hot the food is", when the usual way to express that in English is "The food is hot". If the string is

> "Sometimes, the %1$@ is %2$@.";

> we would translate that into Yoda's English by changing it to

> "Sometimes, %2$@ the %1$@ is."

> or possibly

> "%2$@ the %1$@ is, sometimes."



---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS