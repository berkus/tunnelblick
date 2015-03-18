<h3>Mountain Lion Problems</h3>

Some users are experiencing a problem with Tunnelblick on OS X 10.8 ("Mountain Lion"):
  * They can connect to their VPN server, but they can't use the Internet. Usually this is caused by a DNS problem.

_Note: by "connect" we mean get a successful VPN connection, with the Tunnelblick icon showing an open tunnel._

<font color='red'>The latest "stable" version of Tunnelblick is NOT recommended for OS X 10.8 ("Mountain Lion"), so before doing anything else, please make sure you are using one of the latest beta versions of Tunnelblick from the <a href='DownloadsEntry.md'>Downloads</a> page. (There are currently two "latest" betas. See the <a href='DownloadsEntry.md'>Downloads</a> page for details about which is right for you.)</font>

This document describes some troubleshooting steps you can take and provides a workaround you can use until these problems are fixed.



&lt;hr&gt;



**If you can successfully connect, but you have no Internet access**, please determine if the problem is a DNS problem. The latest beta versions will try to diagnose that if you let them check the computer's apparent public IP address before and after connecting. They will pop up a window telling you that there is a problem with DNS or that the Internet appears to be unreachable after connecting. Allow this with the checkbox on the "Preferences" panel of the "VPN Details…" window.

**Please report problems** on the [Tunnelblick Discussion Group](https://groups.google.com/forum/#!forum/tunnelblick-discuss). Be sure to [include your configuration file and complete Tunnelblick log](https://groups.google.com/d/topic/tunnelblick-discuss/WRhrqIf9brg/discussion).

You can also test for a DNS problem manually. To do that, connect the VPN configuration, then open a browser window and type an IP address of www.google.com in the address bar as follows, then press "return":

> http://173.194.75.147

> (Do not use "ping", "dig", or other commands to test for connectivity -- not all web servers respond to "ping" packets, and some commands use a different mechanism that most of OS X for DNS resolution.)

**If Google doesn't load by IP address, then there is not a DNS problem -- it is something else** and you should look for help in the the links to the left under Troubleshooting, or in the [Tunnelblick Discussion Group](https://groups.google.com/forum/#!forum/tunnelblick-discuss).

**If those pages do load via IP address, it is a DNS problem.**



&lt;hr&gt;


<h3>Fixing DNS Problems</h3>
**The latest beta may solve the DNS problem if you set "DNS/WINS" to "Set nameserver"**. DNS/WINS may be set (for each configuration separately) on the "Settings" tab of the "Configurations" panel of the "VPN Details…" window.

If "Set nameserver" does not work, please try each of the other "Set DNS/WINS" options that are available.

If none of them work for you, try setting your DNS servers manually to Google's public DNS servers, 8.8.8.8 and 8.8.4.4, or OpenDNS's public DNS servers: 208.67.222.222 and 208.67.220.220. You can use these servers at all times. Google public DNS is free, and OpenDNS has a free version. (This will work for most people, but not for  people who need access to a corporate network or DNS service from the VPN's LAN. See below for a solution that may work for that.)

To set your DNS servers manually:
  1. Launch System Preferences,
  1. Click "Network"
  1. Type server addresses, separated by commas, into the box to the right of "DNS Server".
Depending on your version of OS X, you might need to click the "Advanced…" button on the "Network" page, and enter the server addresses in the "DNS" tab of the window that appears.

For example, to specify Google's DNS servers, type "8.8.8.8,8.8.4.4" without the quotation marks.
To specify OpenDNS's DNS servers, type "208.67.222.222,208.67.220.220" without the quotation marks.

**Access to Corporate or Other DNS Servers**

If you need access to the DNS servers on your corporate or other LAN and your OpenVPN setup does not automatically do that (usually they do), there is a way for you to: connect to the VPN, then set the DNS servers manually to the addresses of the DNS servers you wish to use while connected. When you are finished, first disconnect the VPN, and then remove the manual settings. These actions can be automated by using "connected" and "post-disconnect" scripts (see [Using Scripts](cUsingScripts.md)).


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS