# Privacy and Security #





&lt;hr&gt;


## Tunnelblick and VPNs: Privacy and Security ##

Tunnelblick and VPNs are often used for one or more of the following purposes:
  * To protect against eavesdropping and man-in-the-middle attacks when using an untrusted network to access the Internet (for example, from a coffee shop wireless network)
  * To protect against eavesdropping and man-in-the-middle attacks when using the Internet to access  a secured network (for example, accessing a corporate network from home)
  * To make websites think your computer is somewhere it isn't (e.g., accessing UK television programs from non-UK locations)
  * To disguise your IP address from websites
  * To provide anonymous Internet access <font color='red'><== DO NOT use a VPN for this!</font>

Tunnelblick and VPNs in general are great for the first four purposes, <font color='red'>but should not be used to provide anonymous Internet access.</font>

For the rest of this document, when discussion VPNs in general, the term "VPN" will be used. When speaking of Tunnelblick in particular, "Tunnelblick" will be used.

### VPNs and Anonymity -- DON'T! ###
All a VPN can do to help you surf anonymously on the Internet is make your IP address appear to be something different and mix your traffic in with traffic from other users of the VPN. However, there are many ways other than the IP address that websites can use to track you and/or find out who you are. And if a government can access activity logs your VPN service provider keeps, your anonymity can be compromised that way. And powerful organizations that can "tap" the traffic to/from both you and the VPN serviced provider could, even without such logs, correlate your traffic to a VPN service provider and their outgoing traffic to the Internet.

So, <font color='red'>DON'T USE ANY VPN FOR ANONYMITY.</font>**Use [Tor](https://www.torproject.org) or something similar. (And be careful even then: [Tor User Identified by FBI](https://www.schneier.com/blog/archives/2013/12/tor_user_identi.html).)**

### VPNs and Disguised IP Addresses ###
VPNS can disguise your IP address. However, as described above in "VPNs and Anonymity", that usually isn't very helpful by itself.

### VPNs and Location Spoofing ###
A VPN can be used quite successfully to make websites think your computer is located somewhere it isn't. For example, many UK television programs may be accessed via the Internet only from within the UK. The television websites determine whether or not your computer is located in the UK by examining the IP address from which requests are originating. So you can use a UK-based VPN server to "pretend" to be in the UK. Television websites will see your traffic as originating from the VPN server's UK-based IP address and let you watch "Larkrise to Candleford" (or whatever).

### VPNs and Eavesdropping and Man-in-the-Middle Attacks ###
VPNs  can help protect your Internet activity from local eavesdroppers and man-in-the-middle attackers. It does this by encrypting all communications that a local attacker might be able to tap. Your outgoing Internet traffic is encrypted in your computer and is sent in encrypted form to your VPN service provider's computers. There it is decrypted and passed on to the Internet without encryption`*`. Similarly, Internet traffic to your computer arrives at the VPN server without encryption`*`, is encrypted there, and is sent from the VPN server to you in encrypted form. So nobody at your local coffee shop can tell what websites you are using, or read any of your traffic. And nobody on the Internet can see what you are doing on your corporate network.

Sufficiently powerful organizations could eavesdrop and conduct man-in-the-middle attacks if they have access to the VPN server or the connection between the VPN server and the Internet.

`*` If you are using https: all traffic between your computer and the destination website is encrypted, too. But that is separate from the encryption used by the VPN. If you are using https: and a VPN, your traffic is first encrypted for the https:, then for the VPN, then sent to the VPN server. The VPN server removes the VPN encryption, leaving the https: encryption, and then sends the traffic out to the Internet, still encrypted with the https: encryption.

Note: Sufficiently powerful organizations could circumvent your https: encryption by spoofing security certificates.



&lt;hr&gt;


## Tunnelblick Privacy ##

In addition to using OpenVPN to set up, maintain, and tear down a VPN connection, Tunnelblick can also be configured to communicate over the Internet for two other purposes:
  * To check for updates to Tunnelblick itself, optionally sending anonymous profile information about the computer and Tunnelblick setup; and
  * To check for a secure connection and help diagnose problems.

Tunnelblick asks for permission for each of these activities when first launched. The permissions may be modified any other time by changing the appropriate Tunnelblick setting.

Note: Tunnelblick performs these activities by accessing tunnelblick.net, and the tunnelblick.net website keeps logs as described in [tunnelblick.net Logging](#tunnelblick.net_Logging.md).

If you do not want this activity logged, disable update checks and, for all of your configurations, disable checking for apparent IP address changes.

### Check for Updates ###

When checking for updates, Tunnelblick contacts the tunnelblick.net web server. Tunnelblick uses encrypted https: connections to provide security and privacy, but of course the fact that tunnelblick.net was accessed is available to any eavesdropper. That may be avoided by only doing checks for updates manually when connected to a VPN (which, as described above, will hide from local eavesdroppers the fact that tunnelblick.net was accessed).

These update checks are logged by the tunnelblick.net web server. See [tunnelblick.net Logging](#tunnelblick.net_Logging.md) for details.

The setting that controls whether Tunnelblick checks for updates _automatically_ (when launched and every 24 hours thereafter, even if no VPN is connected) is the "Check for updates automatically" checkbox on Tunnelblick's "Preferences" panel.

That panel also has an "Include anonymous profile information" checkbox. If checked, sometimes when checking for updates Tunnelblick will send information to tunnelblick.net about your computer (processor type, amount of RAM, whether you are logged in as an administrator, etc.) and your Tunnelblick setup (number of configurations, how many configurations use "Set nameserver", etc.). The information does not contain anything which identifies users of your computer, but it does contain a randomly-generated unique code that identifies that Tunnelblick installation. The code is generated when Tunnelblick is first run by each user of your computer.

### Check for a Secure Connection and Diagnose Problems ###

Each Tunnelblick configuration has a setting to "Check if the apparent public IP address changed after connecting". If checked, Tunnelblick will send a request to the tunnelblick.net web server before the configuration is connected and will send another request after it is connected.

These requests are done via https:, however:
  * The fact that tunnelblick.net was accessed is available to any eavesdropper because the first request is made before a VPN connection has been established;
  * If an https: connection is not available after connection, Tunnelblick attempts an http: connection using tunnelblick.net's IP address (not its name);
  * The tunnelblick.net web server logs these activities (as do most web servers). See tunnelblick.net Logging for details.



&lt;hr&gt;


## tunnelblick.net Logging ##

All accesses to tunnelblick.net are logged. The logs are kept by the company that provides hosting services to tunnelblick.net. That company does not provide a way to disable logging or delete logs, and it keeps the logs for up to three years. Access to the logs is password protected.

> **Update check requests** send the following information to tunnelblick.net via https:
    * The apparent public IP address and port of the computer (or router the computer with which the computer connects to the Internet)
    * The version of Tunnelblick and the version of Sparkle (the update-checking portion of the program)
    * If the user has agreed, Tunnelblick will also sometimes send anonymous profile information as described above

> **Update information requests**: if an update is available, Tunnelblick will send an HTTPS request to the tunnelblick.net website for information about the update that is to be displayed to the user.

> **Update download requests**: If an update is available and the user agrees, Tunnelblick will download the update from sourceforge.net. The download may be redirected by sourceforge.net to another website or mirror. The update may be downloaded via HTTP or HTTPS. (Updates are digitally signed for additional security, whether or not HTTPS is used.)

> **IP address check requests** send the following information to the tunnelblick.net website:
    * The apparent public IP address and port of the computer (or router the computer with which the computer connects to the Internet)
    * The version of Tunnelblick



---

### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS