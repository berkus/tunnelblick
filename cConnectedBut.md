
## Connects to the VPN, but doesn't work ##
OpenVPN is such a powerful tool with so many options, and computer configurations are so varied, that it is impossible to have an exhaustive troubleshooting guide. This guide is meant for the most common setups, so if it doesn't apply to your situation, or doesn't help, ask the [Tunnelblick Discussion Group](https://groups.google.com/forum/#!forum/tunnelblick-discuss) or the [OpenVPN users mailing list](http://news.gmane.org/gmane.network.openvpn.user) for help.

This page assumes that you are successfully connected to a VPN server. If not, or if you aren't sure, look at [Common Problems](cCommonProblems.md).

<font color='red'><b>Troubleshooting this problem could be very simple: try connecting the VPN with and without "Set nameserver" selected. If one way or the other solves your problem, you're done!</b></font>

## If OpenVPN is connected to the server but your IP address does not change ##
If OpenVPN connects to the server properly but your IP address does not change, you are probably missing the "--redirect-gateway" option. Add the following line:
<pre>     --redirect-gateway def1</pre>
to your configuration file.

By default, OpenVPN only sends some traffic through the VPN -- traffic that is specifically destined for the VPN network itself. The "--redirect-gateway" option tells OpenVPN to send all traffic through the VPN. (Leave out the "--" when it is put in the configuration file.)

An alternative to putting "redirect gateway def1" in the configuration file is to "push" it from the VPN server to the client.

## How to test your IP address ##
You can test find out what IP address your computer is using by going to [https://www.whatismyip.com](https://www.whatismyip.com).

## If OpenVPN is connected to the server but you can't access the Internet ##
If OpenVPN connected to the server properly, but you are having trouble connecting to websites, the first thing to find out is if there is a DNS problem. To check that, try to access a website by using its IP address instead of its name. For example, try "http://129.42.58.216" instead of "http://www.ibm.com" or use some other, known IP address. If the IP address works, but the name doesn't, there is a DNS problem. (Consider the IP address to be "working" if any of the webpage loads.)

**If you have a DNS problem:**
  1. Make sure your network settings don't manually specify a DNS server. If so, it will be used even when the VPN is active. If the manual DNS server is your ISP's DNS server, it is probably set up to ignore queries that come from outside the network. When you are connected to the VPN, your queries come from the VPN server, which is probably outside the ISP's network, so the ISP's DNS server will ignore your request. You should set up your computer to use a free public DNS server (see [How to use a different DNS server](#How_to_use_a_different_DNS_server.md)).
  1. If your DNS settings are specified by DHCP, check your DNS settings both before you connect to the VPN and while you are connected.
    * If the DNS settings are the same, try setting up your computer to use a free public DNS server (see [How to use a different DNS server](#How_to_use_a_different_DNS_server.md)).
    * If the DNS settings are different, the VPN server has successfully "pushed" a DNS server to OpenVPN and that server is being used. Contact the person who maintains your VPN server to find out why that DNS server is not functioning properly.

**If you don't have a DNS problem** then there is something else going on. Ask the [Tunnelblick Discussion Group](https://groups.google.com/forum/#!forum/tunnelblick-discuss) for help.

## How to check your DNS settings ##
  1. Launch System Preferences,
  1. Click "Network"
Your DNS server list is one of the entries on the right. It is a list of IP addresses, separated by commas. OS X will use the first one unless it fails to respond to requests, in which case it will try the second, then the third, etc.

Note: If the DNS server list is dimmed (grayed out), it was set via DHCP, not manually.

## How to use a different DNS server ##
You can set your computer up to use a different DNS server.  [Google Public DNS](http://code.google.com/speed/public-dns/) is free, and [OpenDNS](http://www.opendns.com/) has a free version:
  1. Launch System Preferences,
  1. Click "Network"
  1. Type "8.8.8.8, 8.8.4.4, 208.67.222.222, 208.67.220.220" (without the quotation marks) into the box to the right of "DNS Server"
This will set up your computer to always (whether or not you are connected to the VPN) use two Google DNS servers and two OpenDNS servers (in that order).


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS