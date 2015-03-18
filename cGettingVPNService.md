## Getting VPN Service ##
To use Tunnelblick you need access to a VPN server -- your computer is one end of the tunnel and the VPN server is the other end.

<font color='red'><b>The Tunnelblick project does not provide VPN service</b>
<blockquote>-- we only create the free software that many VPN service providers recommend or provide to their clients.</font></blockquote>

There are several ways to get access to a VPN server:

  * Your employer may provide a VPN server so you can work from home or the road securely.
  * You can set up your own VPN server at home, and use it to access your home network and the Internet securely when at a remote location. The VPN server could be a program running on a Mac, Windows, or Linux computer, or on your home router.
  * You can get (free or for a fee) access to a VPN by using a VPN service provider.

## Employer-provided VPN Servers ##
Your employer should supply you with an OpenVPN configuration file (.ovpn or .conf file), along with the appropriate certificate and key files, or with a [Tunnelblick VPN Configuration](http://code.google.com/p/tunnelblick/wiki/cConfigT) (.tblk, which includes the certificate and key files within it).

Follow the instructions from your employer or in [Installing Tunnelblick](cInstall.md) to install Tunnelblick and configurations.

## Set Up Your Own VPN Server ##
This is more complicated. It involves creating your own OpenVPN configuration file (or modifying the sample file provided by Tunnelblick) and creating your own certificate and key files for encryption. (Tunnelblick versions 3.3 and higher include 'EasyRSA' to help you with creating certificate and key files.) There are tutorials about doing this -- try searching the Internet for "set up openvpn server".

If you want to set up a computer to act solely as a router/bridge/firewall, consider [ZeroShell](http://www.zeroshell.net/eng/). Untangle has a [free VPN component](http://www.untangle.com/store/openvpn.html).

If you have a router running DD-WRT, you can use [OpenVPN on DD-RT](http://www.dd-wrt.com/wiki/index.php/OpenVPN#Enable_OpenVPN_in_the_Router). There is a [tutorial](http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B).

## VPN Service Providers ##
Another way to get access to a VPN server is to use a VPN service provider, an organization that makes its VPN servers available (free or for a fee). Some provide you with a customized, and possibly renamed, version of Tunnelblick.

<table width='100%' border='1'><tr><td>

<table width='100%' border='0'>

<tr><td><b>The following VPN service providers have donated to Tunnelblick:</b></td></tr>
<tr><td> </td><td> </td><td> </td><td> </td></tr>
<tr><td> </td><td> </td><td> </td><td> </td></tr>

<tr><td>Provider</td><td align='right'>Total Donations</td><td align='right'>2014</td><td align='right'>2010-2013</td></tr>
<tr><td> </td><td> </td><td> </td><td> </td></tr>
<tr><td> </td><td> </td><td> </td><td> </td></tr>

<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://my-private-network.co.uk'>My Private Network</a></b></td>   <td align='right'>$1000.00</td> <td align='right'>$500.00</td> <td align='right'>$500.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.kovurt.com'>Kovurt</a></b></td>                         <td align='right'>$850.00</td>  <td align='right'>$600.00</td>       <td align='right'>$250.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://btguard.com'>BTGuard</a></b></td>                            <td align='right'>$770.00</td>        <td align='right'> </td>       <td align='right'>$770.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.surfbouncer.com'>SurfBouncer Personal VPN</a></b></td>   <td align='right'>$300.00</td>  <td align='right'> </td>       <td align='right'>$300.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.ibvpn.com'>ibVPN</a></b></td>                            <td align='right'>$187.00</td>    <td align='right'>$30.00</td>       <td align='right'>$157.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.perfect-privacy.com'>Perfect Privacy</a></b></td>       <td align='right'>$150.00</td>   <td align='right'>$100.00</td>       <td align='right'>$50.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.blackvpn.com'>blackVPN</a></b></td>                     <td align='right'>$100.00</td>  <td align='right'> </td>       <td align='right'>$100.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.hideman.net'>Hideman.net</a></b></td>                   <td align='right'>$100.00</td>  <td align='right'> </td>       <td align='right'>$100.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.trilightzone.org/services.html'>TrilightZone</a></b></td><td align='right'>$100.00</td>  <td align='right'> </td>       <td align='right'>$100.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://provpnaccounts.com'>ProVPNAccounts</a></b></td>              <td align='right'>$50.00</td>   <td align='right'> </td>       <td align='right'>$50.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.missmysoaps.co.uk'>MissMySoaps</a></b></td>              <td align='right'>$20.00</td>   <td align='right'> </td>       <td align='right'>$20.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.banana-vpn.com'>Banana VPN</a></b></td>                  <td align='right'>$19.85</td>    <td align='right'> </td>       <td align='right'>$19.85</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.roadwarriorvpn.com'>Road Warrior VPN</a></b></td>        <td align='right'>$10.00</td>    <td align='right'> </td>       <td align='right'>$10.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://vpnv6.com'>VPNv6</a></b></td>                                <td align='right'>$5.00</td>    <td align='right'> </td>       <td align='right'>$5.00</td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.smallvpn.com'>Small VPN</a></b></td>                                <td align='right'>$3.00</td>    <td align='right'>$3.00</td>       <td align='right'> </td></tr>
</table>

</td></tr></table>

<table width='100%' border='1'><tr><td>

<table border='0'><tr><td>
<tr><td><b>The following VPN service providers recommend or use Tunnelblick exclusively for OS X:</b></td></tr>
<tr><td> </td></tr>
<tr><td> </td></tr>


<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.acevpn.com'>Ace VPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://s6n.org/arethusa'>Arethusa VPN</a></b> <font color='red'>(Free)</font><b></td></tr></b><tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.bucklor.com/'>Bucklor</a></b> <font color='red'>(Free)</font><b></td></tr></b><tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://cloudnymous.com'>cloudnymous</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.comodo.com/home/internet-security/wifi-security.php'>Comodo TrustConnect</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.doublevpn.com/'>DoubleVPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.frozenway.com'>FrozenWay</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.goldenfrog.com/vyprvpn'>Golden Frog Vypr VPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.hostvpn.com/'>HostVPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.ivpn.net'>iVPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.leafyvpn.net'>Leafy VPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.my-expat-network.co.uk'>My Expat Network</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.personalvpn.biz'>Personal VPN Service</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.privateinternetaccess.com'>Private Internet Access</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://proxpn.com'>ProXPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://info.psmail.net/noah'>PSMail</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.raptorvpn.com'>RaptorVPN</a></b> <font color='red'>(Free)</font><b></td></tr></b><tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.shellfire.net/vpn'>ShellFireVPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.slickvpn.com'>Slick VPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://switchvpn.com'>SwitchVPN.com</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://thesafety.us'>TheSafety.US</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.turnkeyvpn.com'>TurnKeyVPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.versavpn.com'>VersaVPN</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://vpnfacile.fr'>VPNFacile</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.vpngate.net/en'>VPN Gate</a></b> <font color='red'>(Free)</font><b></td></tr></b><tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.vpnmaster.com'>VPNMaster</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=https://www.vpnsecure.me'>VPN.S</a></b></td></tr>
<tr><td><b><a href='http://www.tunnelblick.net/to.php?to=http://www.vpnservice.ru'>VPNService.ru</a></b></td></tr>

</td></tr></table>

</td></tr></table>


If you are a VPN service provider that has made a donation or recommends or uses Tunnelblick exclusively for Mac OS X, contact project owner [Jon](http://code.google.com/u/jkbullard/) to be added this list.


Disclaimer: The products, services, and links on this page are not endorsed or recommended by the Tunnelblick developers or Google (host of this website). This list is offered solely for the convenience of those wishing to use Tunnelblick.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS ###