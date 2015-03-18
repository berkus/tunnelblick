## Rebranding Tunnelblick ##

_Note 1: There is an alternate method of distributing Tunnelblick that allows configurations to be automatically installed when Tunnelblick is installed and updated from your web server but does not require rebranding and uses the standard, digitally-signed Tunnelblick application. See [Auto-Install Configurations](cAutoInstall.md) and [Updatable Configurations](cUpdatableConfigurations.md)._

_Note 2: There is a discussion [here](https://groups.google.com/d/msg/tunnelblick-discuss/PuGg6RJH1og/xAZko1IjAR8J) that contains some additional information for rebranding and building Tunnelblick, but note that it is older than this page._

After Tunnelblick 3.3beta21, "Deployed" versions of Tunnelblick must be "rebranded" with a different name. This is done to make sure that different versions of Tunnelblick on one computer do not interfere with each other.

Creating a Deployed Tunnelblick without rebranding (by removing the source code that checks for rebranding) can cause unpredictable behavior, may be less secure, can lead to problems with updating, and can interfere with other installations of Tunnelblick on the same computer. Please don't do it!

To rebrand Tunnelblick you need to be able to build Tunnelblick from the source (see [Building from Source](cBuild.md)). That requires Xcode 3.2.2 running on OS X 10.6.8. Here are step-by-step instructions for rebranding:

First, make sure there are NO SPACES in the path to the source.

Next, edit the source code as follows:

Start Xcode 3.2.2 on Snow Leopard by double-clicking Tunnelblick.xcodeproj.

> Click on the disclosure triangle to the left of the "Resources" folder in the left-most column to expand "Resources"

> Click on "Info.plist" under "Resources" to select it.

> In the right-most column in the document in the right side, change "net.tunnelblick.tunnelblick" to something that doesn't include "net.tunnelblick" -- something like "com.YOUR\_COMPANY\_NAME.NEWPROJECTNAME.deployed-application"

> In the right-most column in the document in the right side, change "https://www.tunnelblick.net/appcast.rss" to something that doesn't include "tunnelblick.net". It should be the URL for an "appcast.rss" used by the Sparkle updater module of Tunnelblick to check for available updates. See the [Sparkle](http://sparkle.andymatuschak.org) documentation for details on the contents of "appacast.rss". (If you override this setting with a forced-preference for "updateURL", that URL cannot contain "tunnelblick.net" either.)

> Quit Xcode, saving all changes (it is important to quit the PROGRAM completely, not just close all the windows)

Start Xcode 3.2.2 on Snow Leopard by double-clicking Tunnelblick.xcodeproj.

> Click on "Tunnelbick" at the top of the list in the left-most column to select it

> Project | Rename<br>
<blockquote>(wait for it to fill in the big box; there will be four items to change  (for <a href='https://code.google.com/p/tunnelblick/source/detail?r=3000'>r3000</a>, which is build 4000))</blockquote>

<blockquote>Rename project to: NEWPROJECTNAME<br>
Click "Rename"</blockquote>

<blockquote>(wait for it to finish)<br>
Click "OK"</blockquote>

<blockquote>Close the window</blockquote>

<blockquote>If Xcode says it failed to save NEWPROJECTNAME.xcodeproj, click "Close"</blockquote>

<blockquote>If an alert window pops up, click "Save"</blockquote>

<blockquote>Quit Xcode (it is important to quit the PROGRAM completely, not just close all the windows)</blockquote>

Remove ....../tunnelblick/build/Tunnelblick.build<br>
<br>
<br>
Double-click NEWPROJECTNAME.xcodeproj.<br>
<br>
<blockquote>In left pane, collapse Classes, Other Sources, and Resources, and then select all three.</blockquote>

<blockquote>Edit | Find | Find in Project (opens "Project Find" window)</blockquote>

<blockquote>Find:    Tunnelblick<br>
Replace: NEWPROJECTNAME<br>
In Selected Project Items<br>
Textual<br>
Contains<br>
Un-check Ignore case<br>
Click "Find"</blockquote>

<blockquote>(wait, it should find 12,035 occurrences (for <a href='https://code.google.com/p/tunnelblick/source/detail?r=3000'>r3000</a>, which is build 4000))<br>
Click "Replace"</blockquote>

<blockquote>Do you really want to replace 12,035 (of 12,035)…<br>
Click "Replace"</blockquote>

<blockquote>(wait for it to finish)<br>
Quit Xcode, saving all changes (it is important to quit the PROGRAM completely, not just close all the  windows).</blockquote>

When rebranding Tunnelblick build 3957 and higher, also change the bundle identifier globally:<br>
<br>
<blockquote>Double-click NEWPROJECTNAME.xcodeproj</blockquote>

<blockquote>In left pane, collapse and highlight Classes, Other Sources, and Resources</blockquote>

<blockquote>Edit | Find | Find in Project (opens "Project Find" window)</blockquote>

<blockquote>Find:    net.tunnelblick.tunnelblick<br>
Replace: YOUR_OWN_BUNDLE_IDENTIFIER <i>(such as "com.example.mac-vpn-client")</i><br>
In Selected Project Items<br>
Textual<br>
Contains<br>
Un-check Ignore case<br>
Click "Find"</blockquote>

<blockquote>(wait, it should get 108 occurrences (for <a href='https://code.google.com/p/tunnelblick/source/detail?r=3000'>r3000</a>, which is build 4000))<br>
Click "Replace"</blockquote>

<blockquote>Do you really want to replace 108 (of 108)…<br>
Click "Replace"</blockquote>

<blockquote>(wait for it to finish)<br>
Quit Xcode, saving all changes (it is important to quit the PROGRAM completely, not just close all the  windows).</blockquote>

Deal with Sparkle update signatures (see <a href='cDigitalSignatures.md'>Digital Signatures</a>):<br>
<ul><li>If you are signing the Sparkle updates, replace ....../tunnelblick/dsa_pub.pem file with your own file.<br>
</li><li>If you are not signing the Sparkle updates, remove the "SUPublicDSAKeyFile" entry from ....../tunnelblick/Info.plist.<br>
Finally, if you are not signing the application yourself, after you have built the rebranded application, copy "tun-signed.kext" and "tap-signed.kext" from the latest beta version of Tunnelblick into your application's "Contents/Resources" folder.<br>
<hr /></li></ul>

<h3>PLEASE USE THE <a href='https://groups.google.com/forum/#!forum/tunnelblick-discuss'>TUNNELBLICK DISCUSSION GROUP</a> FOR COMMENTS OR QUESTIONS