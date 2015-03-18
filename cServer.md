All versions of Tunnelblick allow use of OpenVPN as a server or client (which is determined by the OpenVPN configuration file), but before Tunnelblick version 3.1beta02:
  * Tunnelblick could only start OpenVPN when a user was logged in and launched Tunnelblick; and
  * When the user quit Tunnelblick or logged out, OpenVPN would be shut down.

Tunnelblick version 3.1beta02 and higher are much more flexible:
  * An OpenVPN server or client can be started when the computer starts and keep running until the computer shuts down.
  * Tunnelblick may be used to start or stop the OpenVPN server or client or to edit the configuration file.

To start a connection (either a client or server) when the computer starts:
  1. Share the connection (or make it [Deployed](cCusDeployed.md)). To share a connection, click the "Share configuration" button on the "VPN Details…" window.
  1. Once a configuration is shared, put a check in the "automatically connect" checkbox, and select "when computer starts". The next time the computer is started, the connection will be made even before anyone logs in. You can also start the connection without restarting the computer by clicking the "Connect" button.

Whenever you quit Tunnelblick (or log out, which causes Tunnelblick to quit), it will keep any connections with "when computer starts" selected, but close all other connections (if any).

(To edit the configuration file, the configuration must first be disconnected and made private. Then, after editing, make the configuration shared and connect it.)


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS