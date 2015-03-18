Tunnelblick is made available under the [GNU General Public License, version 2](http://www.gnu.org/licenses/old-licenses/gpl-2.0.html)  ("GPL"). It can be freely distributed within the restrictions of that license.


&lt;hr&gt;


**An easy way to distribute Tunnelblick to multiple clients or servers is to distribute your configurations bundled together with Tunnelblick**. Your configurations will be installed automatically when the user installs the Tunnelblick application and can be automatically updated from your webserver (see [Updatable Configurations](cUpdatableConfigurations.md)).

A simple way to do that is to:
  * Create an empty folder.
  * Copy Tunnelblick.app into the folder.
  * Create a subfolder named ".auto-install" or "auto-install".
  * Copy your [".tblk" configuration files](cPkgs.md) into the subfolder.
  * Control-click the outer folder and select "Compress..." (or compress the folder with any compression utility).
The resulting .zip file may be distributed to users. When the user double-clicks on the Tunnelblick icon in the expanded folder, the user will be asked for a computer administrator's username and password to install both the program and the configurations.

For more details, see [Tunnelblick VPN Configurations](cPkgs.md), especially the [Automatic Installation](cPkgs#Automatic_Installation.md) and [Info.plist](cPkgs#Info.plist.md) sections. See [Updatable Configurations](cUpdatableConfigurations.md) for information on creating and using configurations that can be automatically updated from your website.



&lt;hr&gt;



**You can also distribute configurations without Tunnelblick and have them installed by a simple double-click.**

To do this, your users must first download and install Tunnelblick. Then they can double-click one or more [".tblk" configuration files](cPkgs.md) to install them. You can ["nest"](cPkgs#Nested_Configurations.md) configurations inside an outer configuration so that the user only needs to double-click once to install all of the configurations.



&lt;hr&gt;



**A more complex way of distributing configurations along with Tunnelblick is to create a ["Deployed" version](cCusDeployed.md) of Tunnelblick:**
  * Deployed versions of Tunnelblick **must be [built](cBuild.md) from [rebranded](cRebranding.md) source code** and the rebranded source code must be made available to anyone to whom a binary is "distributed" as defined by the GPL.
  * A "Deployed" version contains, within the Tunnelblick application itself, all of the configurations, certificates, keys, and scripts needed for the connection(s) that you wish to make available.
  * A "Deployed" version can also contain "forced" preferences, which the user is not allowed to override, which can avoid problems caused by users inadvertently changing critical configuration parameters.
  * Because a "Deployed" version contains the configurations within the program,  when the program is updated, the configurations are updated.
  * Any user of the computer can connect using the configuration(s).


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS