http://code.google.com/p/tunnelblick/downloads/detail?name=Tunnelblick_3.3beta22_Unsigned.dmg#summary Installing Tunnelblick
#sidebar cSb



## Installing Tunnelblick ##

The Tunnelblick application contains the Tunnelblick GUI, OpenVPN, and OpenSSL, so no other installations are needed.

**Special note for those who may have installed RaptorVPN or Urban Shield VPN, VPN In China, or certain other VPN software**: These installations have backups that must be removed before installing or reinstalling Tunnelblick unless you are continuing to use the same service. [Uninstalling Tunnelblick](#Uninstalling_Tunnelblick.md) will remove these backups. See [this Discussion Group thread](https://groups.google.com/d/topic/tunnelblick-discuss/s368xGP5Qpk/discussion) for details.

First, download the latest disk image from the [Downloads page](DownloadsEntry.md). Double-click the downloaded .dmg file. An icon for a "Tunnelblick” disk will appear on the Desktop, and a window similar to the following will appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-dmg-2010-10-16.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-dmg-2010-10-16.png)

Double-click the Tunnelblick icon and a new window will appear.



&lt;hr&gt;



If the window is similar to the following:

![http://tunnelblick.googlecode.com/files/cinstall-02-app-store-only-2013-07-27.png](http://tunnelblick.googlecode.com/files/cinstall-02-app-store-only-2013-07-27.png)

then your security settings do not allow you to open files that are not from the Mac App Store by double-clicking. You should click "OK" (the window will disappear), then Control-click the Tunnelblick icon and click "Open" to open the file. A new window will appear.



&lt;hr&gt;



If the window is similar to the following:

![http://tunnelblick.googlecode.com/files/cinstall-06-from-internet-2013-07-27.png](http://tunnelblick.googlecode.com/files/cinstall-06-from-internet-2013-07-27.png)

then click the "Open" button to continue. The window will disappear and a new window will appear.



&lt;hr&gt;



If the window is similar to the following:

![http://tunnelblick.googlecode.com/files/cinstall-05-convert-configs-2013-07-27.png](http://tunnelblick.googlecode.com/files/cinstall-05-convert-configs-2013-07-27.png)

then you have OpenVPN configurations that have not been converted to Tunnelblick VPN Configurations.

Tunnelblick 3.3beta22 and higher only use Tunnelblick VPN Configurations because OpenVPN configurations are difficult to secure properly. When a configuration is converted, all of the original files used by the OpenVPN configuration are collected into the Tunnelblick VPN Configuration and then the Tunnelblick VPN Configuration is secured.

  * **Ignore** will ignore any OpenVPN configurations. They will not be available for use in Tunnelblick -- they will not appear in the list of configurations.<br />
  * **Quit** will quit Tunnelblick.<br />
  * **Convert Configurations** will attempt to convert your configurations before installing Tunnelblick. If the conversion fails, Tunnelblick will not be installed.<br />

Click **Ignore** or **Convert Configurations**. The window will disappear and a new window will appear.



&lt;hr&gt;



A window similar to the following window should now be displayed:

![http://tunnelblick.googlecode.com/files/cinstall-03-must-be-in-apps-2013-07-27.png](http://tunnelblick.googlecode.com/files/cinstall-03-must-be-in-apps-2013-07-27.png)

If you are reinstalling, upgrading, or downgrading Tunnelblick, the window will show the version number of the current copy and of the new copy. The current copy of Tunnelblick will be put in the Trash before it is replaced.

The name and password of a computer administrator is needed to install Tunnelblick. Tunnelblick's imbedded OpenVPN needs root privileges because it needs to modify network settings by configuring new network devices, changing routes, and adding and removing nameservers. Because we don't want you to enter your administrator account name and password every time you start a VPN connection, Tunnelblick comes with a setuid root binary that allows it to start a VPN connection with super user rights. Tunnelblick uses your administrator account name and password so it can create this setuid root binary. Tunnelblick also secures itself from being modified.

Click the "Install" button to install Tunnelblick to your hard drive. Conversion of OpenVPN configurations to Tunnelblick VPN Configurations, if requested, will be done before the installation so that if they fail the installation will not take place and any existing Tunnelblick installation will not be changed.

After the conversion and installation is complete (it may take a couple of seconds to install, but if conversions are done they can take tens of seconds), a new window will appear.




&lt;hr&gt;



If the new window is similar to the following:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-launch-2010-10-16.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-launch-2010-10-16.png)

Click the "Launch" button to launch Tunnelblick



&lt;hr&gt;



If Tunnelblick is currently running, a window similar to the following will appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-running-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-running-2010-02-06.png)

(Note: Connections marked "automatically start when computer starts" **will not be closed**.)

Then click the "Close VPN Connections and Stop Tunnelblick" to continue. After all connections are closed and Tunnelblick has quit, the new version of Tunnelblick will be launched. Continue with the following sections.



&lt;hr&gt;



## The First Time Tunnelblick is Run by Each User ##
If this is the first time you have run Tunnelblick as a particular user, or the first time after certain Tunnelblick upgrades, the following window may appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-check-2010-02-06.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-check-2010-02-06.png)

**Tunnelblick checks for updates by making a request to the tunnelblick.net website** each time it is launched, and every 24 hours thereafter. As part of its normal website operation, the website keeps a log which includes information about such requests. The log includes the date and time of the request, the public IP address from which the request originated, and the version of Tunnelblick that made the request. **The request doe not contain any personally identifiable information.** (The information that is sent is similar to the information that is sent to a website when you use a browser to look at a page on the Internet, and the log that the website keeps is similar to logs kept by most websites.) If "Include anonymous system profile" is checked, Tunnelblick also sometimes includes information about your computer and Tunnelblick's settings in the request. You can see what information is included by clicking on the "disclosure triangle" to the left of the checkbox.

Specify whether or not you wish to have Tunnelblick check for updates each time it is launched. Each time an update is available, you will be given a choice of whether to install the update or not.

At any time after installation, you may check for an update by clicking the "Check Now" button in the "Updates" section of the "Preferences" panel of the "VPN Details…" window.



&lt;hr&gt;



If this is the first time you have run Tunnelblick as a particular user, or the first time after certain Tunnelblick upgrades, the following window may appear:

![http://tunnelblick.googlecode.com/files/cinstall-07-ip-check-query-2013-07-27.png](http://tunnelblick.googlecode.com/files/cinstall-07-ip-check-query-2013-07-27.png)

Checking if your computer's apparent public IP address changes when you connect to a VPN may help insure that your configuration is correct, and may help Tunnelblick diagnose DNS problems.

**Tunnelblick does this checking by making a request to the tunnelblick.net website** before each attempt to connect to a VPN and after a successful connection is made. As part of its normal website operation, the website keeps a log which includes information about such requests. The log includes the date and time of the request, the public IP address from which the request originated, and the version of Tunnelblick that made the request. **The request doe not contain any personally identifiable information.** (The information that is sent is similar to the information that is sent to a website when you use a browser to look at a page on the Internet, and the log that the website keeps is similar to logs kept by most websites.)

Click "Check for a Change" or "Do Not Check for a Change", as you wish.

At any time after installation, you may specify whether or not Tunnelblick checks for a change on the "Preferences" panel of the "VPN Details…" window.



&lt;hr&gt;



When there are no configurations (which is usually the case the first time Tunnelblick is run by each user when using a non-deployed version of Tunnelblick with no Shared configurations), the configuration helper will appear:

![http://tunnelblick.googlecode.com/files/using-tunnelblick-welcome-2010-07-29.png](http://tunnelblick.googlecode.com/files/using-tunnelblick-welcome-2010-07-29.png)

Click the appropriate button and the configuration helper will guide you through the installation of configuration files.



&lt;hr&gt;



## Launching Tunnelblick ##
To launch Tunnelblick after setting up configuration and other files, double-click Tunnelblick in the `Applications` folder.

If Tunnelblick is running when you log out, shut down, or restart your computer, it will automatically be launched when you log in. Otherwise you will have to launch it manually when you need it.



&lt;hr&gt;



## Uninstalling Tunnelblick ##

_Note: **You do not need to uninstall Tunnelblick before updating or reinstalling**. You should uninstall if you no longer want to use Tunnelblick, or if you are having problems and have been told to uninstall it._

If you intend to re-install Tunnelblick, be sure you have a backup of your Tunnelblick configuration files and key and certificate files -- the .ovpn, .key, .crt, and/or .tblk files, and make a note of any configuration settings and appearance and other preferences you have set up. (They will be lost.)

The uninstall program can do a "test", which does not uninstall anything, but displays a log of what it would have done if it were uninstalling.

Download an uninstaller disk image from the [Downloads](DownloadsEntry#Tunnelblick_Uninstaller.md) page and double-click it. (The uninstall program may be used to uninstall any version of Tunnelblick or any version of any rebranded version of Tunnelblick.)

**First, if you have already partially uninstalled (manually by dragging the application to the Trash, or with AppCleaner or something similar):**

  * Disconnect all configurations and quit Tunnelblick (or the rebranded program)<font color='red'><code>*</code></font>
  * Install (again, that is, re-install) Tunnelblick or the rebranded program (whatever program you want to uninstall). It is important that you install to the same location as the original installation. If you are uninstalling a "Deployed" version of Tunnelblick, you must install [Tunnelblick 3.3beta21b Unsigned (build 3114.3185)](http://code.google.com/p/tunnelblick/downloads/detail?name=Tunnelblick_3.3beta22_Unsigned.dmg), which can be installed even if there is a "Deployed" version installed or partially installed.
  * Launch Tunnelblick, disconnect from all VPNs, then quit Tunnelblick.

**Now, to uninstall Tunnelblick located in /Applications:**
  * Disconnect all configurations and quit Tunnelblick<font color='red'><code>*</code></font>
  * Double-click the "Uninstaller"
  * Click on "Test" or "Uninstall"

**Or, to uninstall Tunnelblick located somewhere other than /Applications, or to uninstall RaptorVPN, Urban Shield VPN, or other rebranded Tunnelblick:**
  * Disconnect all configurations and quit Tunnelblick (or the rebranded program)<font color='red'><code>*</code></font>
  * Drag and drop the "Uninstaller" to your Desktop
  * Drag and drop the application you want to uninstall (Tunnelblick or a rebranded program) to the "Uninstaller" on your Desktop
  * Click on "Test" or "Uninstall"

**Finally, restart your computer.**

<font color='red'><code>*</code></font> If you get a "spinning beachball" when you click the Tunnelblick icon, that usually means that Tunnelblick has a window open and is waiting for your response. Minimize or close the windows of all other applications (and in all Spaces) to expose the window. If Tunnelblick does not have an open window, you will have to force Tunnelblick to quit. Follow the procedure described in [this discussion](https://groups.google.com/d/topic/tunnelblick-discuss/CcqADLK5Ttg/discussion) in the Tunnelblick Discussion Group.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###