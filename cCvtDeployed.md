<h3>Converting a "Deployed" version of Tunnelblick to a "regular" Version</h3>





&lt;hr&gt;


## Why You May Want to Do This ##

The latest versions of Tunnelblick include important security changes. These changes modified the way that "Deployed" versions of Tunnelblick are created and are difficult for some VPN service providers to implement, so some of them continue to supply old "Deployed" versions to their users.

If you are using such an older "Deployed" version of Tunnelblick, you may want to convert to using a non-Deployed version so that you can use the latest versions of Tunnelblick which include the security changes.

_Note: Installing a Deployed version of Tunnelblick will "poison" an already-installed "regular" version. If you do so, it will be necessary to follow these instructions again, especially the "completely uninstall Tunnelblick" part of the instructions._

If you are a VPN service provider distributing older Deployed versions of Tunnelblick, you may want to update them or change to using "automatically installed" configurations with a regular version of Tunnelblick. See [Distributing Tunnelblick](cDistribute.md) for details.



&lt;hr&gt;


## How To for Experts ##
  1. Copy (do not move)<br><b>Tunnelblick.app/Contents/Resources/Deploy</b><br>to the Desktop.<br>
<ol><li><a href='cInstall#Uninstalling_Tunnelblick.md'>Completely uninstall Tunnelblick</a>.<br>
</li><li>Install the latest version of Tunnelblick from <a href='DownloadsEntry.md'>Tunnelblick Downloads</a>. Launch Tunnelblick and proceed normally; quit when you are asked about configurations<br>
</li><li>Copy the contents of the Deploy folder (not the folder itself) on the Desktop into<br> <b>~/Library/Application Support/Tunnelblick/Configurations</b> <i>(note the "~")</i>
</li><li>Launch Tunnelblick and allow the configurations to be converted.<br>
</li><li>Enjoy!<br>
<br>
<br>
<hr><br>
<br>
<br>
<h2>How To for Everyone Else</h2>
You can use the following instructions to convert from using a Deployed version of Tunnelblick to using a "regular" version. These are extremely detailed, click-by-click instructions:</li></ol>

<ol><li>Extract the configurations from the Deployed version of Tunnelblick and save them:<br>
<ol><li>Find the copy of Tunnelblick.app that you are using. It may be in /Applications, but older versions of Tunnelblick (before version 3.3beta22) can be installed anywhere.<br>
</li><li>Control-click (hold down the "control" key on the keyboard and click) on Tunnelblick.app and select "Show Package Contents". A new Finder window will appear with the single folder "Contents".<br>
</li><li>Double-click on "Contents", and the window will change to include several items.<br>
</li><li>Double-click on "Resources", and the window will change to include many items (usually more than 70)<br>
</li><li>Find the folder named "Deploy" and Option-drag it to an empty space on the Desktop (that is, drag the folder while holding down the "option" key). This will create a new copy of the folder on the Desktop.<br>
</li></ol></li><li>Completely uninstall Tunnelblick, <b>using the instructions at <a href='cInstall#Uninstalling_Tunnelblick.md'>Uninstalling Tunnelblick</a></b>. <font color='red'><b><== CRITICAL</b></font>
</li><li>Install a recent version of Tunnelblick:<br>
<ol><li>Download a new version of Tunnelblick from <a href='DownloadsEntry.md'>Tunnelblick Downloads</a>.<br>
</li><li>Install it by double-clicking on the "Tunnelblick.app" icon. (Depending on your browser, you may need to find and double-click on the downloaded Tunnelblick.dmg file first.)<br>
</li><li>When asked for your username and/or password, provide your computer administrator username/password, not your VPN password.<br>
</li><li>Answer the questions about updating Tunnelblick and checking for IP address changes as you wish.<br>
</li><li>Quit Tunnelblick when you are asked a question about configurations.<br>
</li></ol></li><li>Prepare to use the saved VPN configurations you saved in step 1.<br>
<ol><li>Open the user's "Library/Application Support/Tunnelblick/Configurations" folder:<br>
<ol><li>Open a new Finder window.<br>
</li><li>Hold down the "option" key on the keyboard and click on the "Go" menu item. Keeping the "option" key held down, click on "Library", then release the "option" key. The Finder window will change to show the "Library" folder.<br>
</li><li>Double-click the "Application Support" folder.<br>
</li><li>Double-click the "Tunnelblick folder".<br>
</li><li>Double-click the "Configurations" folder. The window should be empty because there are no configurations.<br>
</li></ol></li><li>Double-click the "Deploy" folder on your Desktop. A Finder window will appear with the files and folders that contain your VPN configurations.<br>
</li><li>Option-drag everything in that window to the empty "Configurations" Finder window.<br>
</li></ol></li><li>Convert the OpenVPN configurations to be Tunnelblick VPN Configurations:<br>
<ol><li>Launch Tunnelblick. You will be asked if you want to convert the configurations. Click the button to "Convert".<br>
</li><li>(There is no step 2!)<br>
</li></ol></li><li>Enjoy!</li></ol>

Please report any problems with these instructions to the <a href='https://groups.google.com/forum/#!forum/tunnelblick-discuss'>Tunnelblick Discussion Group</a>.<br>
<br>
<hr />

<h3>PLEASE USE THE <a href='https://groups.google.com/forum/#!forum/tunnelblick-discuss'>TUNNELBLICK DISCUSSION GROUP</a> FOR COMMENTS OR QUESTIONS</h3>