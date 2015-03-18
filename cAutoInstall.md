## Auto-Install Configurations ##
You can distribute Tunnelblick with configurations that will be installed automatically when Tunnelblick itself is installed. The alternate does not require rebranding and uses a standard, digitally-signed Tunnelblick.app, however, it cannot update configurations the way that a [Deployed](cCusDeployed.md) version can.

When Tunnelblick installs itself, it looks for configurations to install in the "auto-install" and ".auto-install" folders that are in the same location as Tunnelblick.app.

  1. Create a Tunnelblick VPN Configuration (".tblk") for each configuration that you wish to distribute. As usual, the name of the .tblk will be what is displayed to the user as the name of the configuration. (You may create a folder structure that contains some or all of the configurations in subfolders.)
  1. Create a folder, named "YOURNAMEConfigurations", and move all the Tunnelblick VPN Configurations into it. (Move the entire folder structure of configurations if you created one.)
  1. Rename the folder to "YOURNAMEConfigurations.tblk".
  1. Create a second folder, named "auto-install" and move "YOURNAMEConfigurations.tblk" into it. (Name the folder ".auto-install" if you want to hide it from your users.)
  1. Create a third folder, named "YOURNAME", and move "auto-install" or ".auto-install" into it.
  1. Download a Tunnelblick.dmg from the Tunnelblick Downloads page at https://code.google.com/p/tunnelblick/wiki/DownloadsEntry. Version 3.3beta52 or higher is recommended (versions below it may have security vulnerabilities).
  1. Double-click the .dmg to open it, and drag the Tunnelblick icon into the third folder ("YOURNAME") to copy Tunnelblick.app (the Tunnelblick application) into that folder.

The "YOURNAME" folder now contains the following:
> Tunnelblick.app
> auto-install
> > (your configurations, perhaps in subfolders)

Finally, create a .zip of the "YOURNAME" folder by control-clicking the "RiseupYOURNAME folder and clicking on "Compress YOURNAME". A "YOURNAME.zip" file will be created.

That "YOURNAME.zip" file is what users should download.

(Or you can create a .dmg that contains the contents of the "YOURNAME" folder. That's more complicated and not explained here.)


---


USER INSTRUCTIONS

After downloading "YOURNAME.zip", users may need to double-click the .zip file to expand it (their OS or browser may do that automatically).

A Finder window will appear with two items: Tunnelblick.app and a folder named "autoinstall". To start the process, they need only double-click Tunnelblick.app.

After finishing the installation, they may discard the "YOURNAME" folder and/or the "YOURNAME.zip" file if they wish.





---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS