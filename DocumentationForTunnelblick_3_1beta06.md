

&lt;hr&gt;


<font size='3'><b><a href='http://tunnelblick.googlecode.com/files/Tunnelblick_3.1beta06.dmg'>Download Tunnelblick 3.1beta06</a></b></font>


&lt;hr&gt;



**[Full Release Notes](RlsNotes.md)**

## What's New in Tunnelblick 3.1beta06 (from 3.1beta04) ##
  * Takes into account both the 'dev-type' and 'dev' options in the configuration file when trying to determine if it is a 'tun' or 'tap' connection. Tunnelblick tries to determine that so it can load only the tap or tun kext (device driver) that is required. Note: there appears to be a bug in OpenVPN that makes the dev-type option fail; this does not help that problem.

  * Runs new scripts, pre-connect.sh and post-disconnect.sh, as root before connecting and/or after disconnecting if the scripts exist. (They must be in a .tblk package). This allows manipulation of kexts and/or the network configuration before the tun/tap kexts are loaded and OpenVPN is run and after OpenVPN exits and the kexts are unloaded.

  * Changed "Online Documentation.webloc" that is put in the .dmg so it will go to the new main documentation page.

  * Fixes bug that caused .conf configuration files to be ignored.

  * Fixes bug that caused failure to connect if "Monitor connection" was checked and the standard up script was used.

  * Fixes bug that caused restarts to fail if a different configuration was disconnected at exactly the right (or wrong!) time.

  * Fixes bug that didn't clean up when installation of a .tblk package failed.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](http://groups.google.com/group/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS