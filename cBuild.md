**HOW TO BUILD TUNNELBLICK FROM THE SOURCE CODE**



_Note: This page has not been updated for a long time; there is a discussion [here](https://groups.google.com/d/msg/tunnelblick-discuss/PuGg6RJH1og/xAZko1IjAR8J) that contains some updates and tips for rebranding and building Tunnelblick._

## INTRODUCTION ##

Usually, people install and use a "release" -- an easy-to-use version -- of Tunnelblick. The most recent release is always on the <a href='http://code.google.com/p/tunnelblick/wiki/DownloadsEntry?tm=2'>Downloads</a> page and is a .dmg file. It's easy to install Tunnelblick from this .dmg.

As project developers and members make changes (bug fixes and improvements) to Tunnelblick, they are added to the source code and tested. When "enough" (whatever that means) changes have been made and tested, a new release is prepared by the Tunnelblick project developers and made available.

Sometimes, especially when changes are extensive, a "beta", or testing, release is prepared and made available to everyone brave enough to try it. The beta version allows for more thorough testing by more people, and the beta label warns people that the version is not fully tested and that they should be careful using it.

Because Tunnelblick is distributed using the "GPL" license, the source code itself is also available, including the source code for changes before they are incorporated into a release. That means that anyone with sufficient technical skills can create their own release and test it or use it as they see fit. Following are brief instructions for doing that.

**These instructions are very long because they are very detailed.**

## PRELIMINARY STEPS ##
First, you need to be running Snow Leopard (OS X 10.6.x). Although Tunnelblick will run on Tiger (OS X 10.4.x) and Leopard (OS X 10.5.x) as well as Snow Leopard and Lion, it is built (developed and compiled) into a release on Snow Leopard, because only Snow Leopard supports the both the PPC processor and the 32/64-bit version of "tuntap", third-party software used by Tunnelblick to make network connections. The 32/64-bit version of tuntap is required to run Tunnelblick on Snow Leopard using the 64-bit kernel.

For tips on building Tunnelblick on Lion (OS X 10.7.x), see [Building on Lion](#BUILDING_ON_LION.md).

(Prior to Tunnelblick source code [revision 232](https://code.google.com/p/tunnelblick/source/detail?r=232), you needed to be running Leopard and Xcode 3.1.1 or above to build Tunnelblick. See ["Building on Leopard"](#BUILDING_ON_LEOPARD.md).)

Second, you must download and install Xcode 3.2.2 if it isn't already installed on your computer. (To determine if it is already installed, use Spotlight to search for "Xcode.app", start it, and check the version number. Start Xcode and click "Xcode", then "About Xcode" and make sure it is version 3.2.2.) If you don't have Xcode, download the version for Mac-only development from http://developer.apple.com/technology/xcode.html. (A free ADC membership is required for the download.) It downloads as a huge - about 800MB(!) - disk image (.dmg) file. Install it, as usual, by double-clicking the .dmg and then double-clicking "XcodeTools.mpkg" and following the instructions.

Xcode versions later than 3.2.2 may be used, but they do not generate code for PowerPC processors.

## DOWNLOAD THE SOURCE CODE ##
Third, you must download the Tunnelblick source code. Start a terminal session (double-click "Terminal" in the Applications folder). Type the following into the Terminal window: "cd " (without the quotes). That is, the letter c, the letter d, and a space. Open a new Finder window by clicking on Finder in the Dock. Navigate to the place you would like to save the Tunnelblick source code (your Documents folder, for example, or the Desktop) and then hold down the command key on the keyboard (the cloverleaf or apple key) and press the up-arrow key once. You now have a view of the folder which contains the folder you want to store the source code in (and it contains other things, too). Drag the folder in which you want to store the source code to the Terminal window, then let release it. The path to the folder you want to store the source code will be automatically typed for you! Click on the Terminal window, then press the "return" key. Click and drag the following line into the terminal window, too:

svn checkout http://tunnelblick.googlecode.com/svn/trunk/ tunnelblick-read-only

and press the "return" key. This will download the latest version of the Tunnelblick source code from the web and store it in a new folder named "tunnelblick-read-only". ("read-only" means that you cannot commit any modifications you make back to the repository. It does NOT mean that the copy you get is "read only" as far as making changes to it.) Remember, the latest version has not been tested thoroughly, so you take your chances!

To get an older version of the source code (for example, for a release), see [Getting source code for Tunnelblick](cGettingSource.md).

## SET XCODE TO CREATE A "RELEASE" ##
Tunnelblick versions after 3.2beta10 can be built as a "Signed Release", an "Unsigned Release", or as "Debug". Under most circumstances, a "Signed Release" should be built. An "Unsigned Release" should be built and the code signed manually if a Deployed version of Tunnelblick will be created from the build result and users will be able to save username/password/passphrase in the Keychain. See [Tunnelblick and Digital Signatures](cDigitalSignatures.md) for details.

You should set up Xcode to create a "Signed Release" or "Unsigned Release" build instead of a "Debug" build. Navigate to the "tunnelblick-read-only" folder that was created above, double-click the the "tunnelblick" folder within it, then double-click "Tunnelblick.xcodeproj". That will start Xcode in a new window with the Tunnelblick project. Click "Build" in the menu bar, then click "Build Results". That will open a new window. In that window click on the drop-down button at the top left that says something like "10.6 | Debug | Tunnelblick | i386", and under the "Active configuration" heading, click on "Signed Release". The button should now read "10.6 | Signed Release | Tunnelblick | i386".

Don't worry about the "10.6"; Tunnelblick will still be built for OS X 10.4 - 10.9. The "10.6" refers to the SDK that is used. System methods introduced after 10.4 are only used if they exist (that is, if Tunnelblick is being executed on a version of OS X that supports them).

## BUILD A RELEASE ##
Finally! You are ready to build a release of Tunnelblick. In the "Build Results" window, click the "Build" button. The build process will start, and a series of status messages will be displayed. There should be no errors, but see [BUILD WARNINGS](#BUILD_WARNINGS.md) about warnings that are considered "normal".

The first time a build is done, it may take several minutes, even on a relatively fast computer, so be patient. (Subsequent builds, which do not usually rebuild OpenVPN or the Tun/Tap kexts, are quicker.)

When the build is complete, "Build succeeded" will appear at the bottom of the Build Results window. (It takes another 30-60 seconds to finish creating the .dmg file after "Build succeeded" appears). You have made a Tunnelblick release!

If you have not installed Rosetta before starting the build, OS X will prompt you to do so. It may be necessary to redo the build in this case. Before you rebuild, delete the "tunnelblick-read-only/tunnelblick/build" folder and the "tunnelblick-read-only/third\_party/built" document, to ensure a complete, clean, build.

At this point, you might want to make a copy of your current Tunnelblick.app in case the new one doesn't work for you.

Your release .dmg file is at tunnelblick-read-only/tunnelblick/build/Release/Tunnelblick.dmg. Double-click it and, in the resulting window, drag the Tunnelblick.app to the Applications shortcut to copy it to your Applications folder. Or see more detailed instructions for installing and using Tunnelblick in "Using Tunnelblick", which is contained in the .dmg file.

Good luck!

## DIGITAL SIGNATURES ##
Digital signatures are available in Tunnelblick 3.2beta12 and later.

You cannot digitally sign as if you were the Tunnelblick project issuing an official release, but you can add your own digital signature if you wish.

If you _don't_ add your own digital signature:
  * The built application will not include any digital signature.
  * Warnings will be issued during the build process. (You can ignore these warnings).
  * When the built application is used, users will be asked to grant the program access to each item saved in the user's Keychain.

To add your own digital signature to the built application, simply create a signing certificate with Common Name 'TunnelblickSigning' using Keychain Access (see instructions at http://developer.apple.com/library/mac/#documentation/Security/Conceptual/CodeSigningGuide/Procedures/Procedures.html#//apple_ref/doc/uid/TP40005929-CH4-SW1). A certificate with that Common Name will be used automatically by the build scripts.

## BUILD WARNINGS ##
  * **As of [r1464](https://code.google.com/p/tunnelblick/source/detail?r=1464), there should be no warnings issued when Tunnelblick is built. It is still necessary to "Clean all" before building, however.**

  * For versions of Tunnelblick prior to [r1021](https://code.google.com/p/tunnelblick/source/detail?r=1021), Xcode 3.2.2 causes four warning messages from the linker to appear when building. After completing a build, click "Build", then "Clean All Targets", then, with checks in both checkboxes, click "Clean". Builds after that will not have the error. (Note: you have to build, then clean. Just cleaning doesn't help.) After you clean, you have to build again, of course.
  * Build 2013 and higher causes eight warning messages to appear when building OpenVPN. These warnings may be ignored. There are three 'incompatible pointer type' and one 'assignment discards qualifiers'; each warning is repeated twice (once each for PowerPC and intel.)
  * Otherwise, three or four warnings are normal, all complaining about "Object file compiled with -mlong-branch...". (These warnings come from a bug in Apple's Software Development Kit and can be ignored.)

> So the first time Tunnelblick is built from source:
  * For versions of Tunnelblick prior to [r1021](https://code.google.com/p/tunnelblick/source/detail?r=1021), there will be 16 warnings. After that (unless a third\_party component is modified), there will be eight warnings until a "Clean All Targets" is performed. After that, there will be four warnings each time Tunnelblick is built.
  * For versions of Tunnelblick after [r1020](https://code.google.com/p/tunnelblick/source/detail?r=1020), there will be 12 warnings. After that (unless a third\_party component is modified), there will be four warnings each time Tunnelblick is built.
  * Versions that include OpenVPN 2.3alpha have a large number of warnings (64) that may be ignored.

  * Warnings during the build process that a target is already signed may appear if building the application but not rebuilding that particular target. These warnings may be ignored.

## BUILDING OPENVPN AND OTHER THIRD-PARTY SOFTWARE ##
The normal Tunnelblick build process builds all of the third-party software (OpenVPN, OpenSSL, LZO, Spakle, pkcs11-helper, and tuntap) using third\_party/Makefile.

Unlike the usual "Make" procedure, the third\_party/Makefile creates special "built-xxx" files to indicate that each of the components has been built, and a "built" file to indicate that everything has been built. After that first build of Tunnelblick, the presence of the "built" file and the "built-xxx" files causes the build process to skip building third party components.

What this means is that if you modify any of the third-party source after building Tunnelblick, you must delete the corresponding "built-xxx" file so that Tunnelblick will rebuild that software when you next build Tunnelblick.

## BUILDING ON LEOPARD ##
It is possible to build versions of Tunnelblick prior to [r232](https://code.google.com/p/tunnelblick/source/detail?r=232) on Leopard. The instructions above should be followed, except:
  * Xcode 3.1.1 or higher is required.
  * To download [r231](https://code.google.com/p/tunnelblick/source/detail?r=231) (the last version which can be built on Leopard), use the following command instead of the command given above (note the change in boldface):

> svn checkout http://tunnelblick.googlecode.com/svn/trunk/ **-r 231** tunnelblick-read-only

## BUILDING ON LION ##
Current versions of Tunnelblick are built on OS X 10.6 ("Snow Leopard") with Xcode 3.2.2, as described above. That is because higher versions of Xcode do not support PowerPC processor builds. At some point, perhaps in Tunnelblick 3.3, PowerPC and/or OS X 10.4 support will be dropped, and Tunnelblick will be built on OS X 10.7 and/or 10.9 ("Lion" and/or "Mavericks").

To build on Lion (with the understanding that PowerPC Macs and Macs with OS X 10.4 will not be able to execute the resulting binary), see [this discussion](https://groups.google.com/d/msg/tunnelblick-discuss/vJYGdD-et4k/MFM1a-7Dt2QJ).

---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS