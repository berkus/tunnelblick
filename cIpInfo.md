## Detecting IP Address Changes ##
Tunnelblick can check that the computer's "apparent public IP address" changes after connecting to a VPN, which is what most users want to happen.

The "apparent public IP address" (APIPA) is the address that the computer presents when it requests something on the Internet (its return address). When a computer asks for a web page, for example, it tells the web server to reply to a public IP address. The word "apparent" is used because the APIPA isn't the IP address of the computer itself (which may be on a LAN and have a private IP address such as 192.168.0.123), but it is the IP address of the computer as far as the outside world is concerned.

This feature can be enabled or disabled using a checkbox on the "Preferences" panel of Tunnelblick's "VPN Details…" window.

## If the IP Address Does Not Change ##
If the computer's APIPA does not change, it may be due to an error or omission in the OpenVPN configuration. By default, OpenVPN only sends traffic through the VPN that is destined for the VPN. Normal traffic to websites, for example, is _not_ sent through the VPN. That can be changed, to send all traffic through the VPN, by using OpenVPN's "--redirect-gateway" option.

If the OpenVPN configuration file (and the options pushed to the computer by the OpenVPN server) do not include the "--redirect-gateway" option, Tunnelblick can supply the "--redirect-gateway def1" version of the option if you check the "Route all traffic through the VPN" checkbox on the "While Connected" tab of the "Advanced" settings page for the configuration.


## Technical Details ##
Tunnelblick detects the change by determining the computer's APIPA before connecting and comparing it with the APIPA five seconds after the connection succeeded.

Tunnelblick determines the APIPA by sending a "GET" request to "http://tunnelblick.net/ipinfo". That web page returns a webpage that consists of three strings separated by commas: the APIPA, port to which the reply was directed (additional info available to the webserver, but probably not of any value), and the IP address of the tunnelblick.net webserver itself.

Five seconds after a successful connection, Tunnelblick sends another identical "GET" request. If there is a response and the APIPA has not changed, the user is notified by a pop-up alert window.

If there is no answer within 30 seconds, it is assumed that either DNS is not working or access to the Internet in general is impaired. To determine which, Tunnelblick sends a "GET" request using the IP address of the tunnelblick.net webserver that was returned by the pre-connection "GET" request. If that request succeeds, it means that DNS was not able to resolve the "tunnelblick.net" name, so there is a DNS problem. If that request fails, it means that the computer is unable to access the tunnelblick.net server directly, which usually indicates a problem reaching the Internet in general. That is usually a symptom of a routing problem.

Note that there could be other reasons that the tunnelblick.net webpage is not available. There could be a problem with the tunnelblick.net server, or there could be a firewall that blocks access to that server.

## Customization ##
The URL that Tunnelblick uses for the "GET" request is contained in the "IPCheckURL" entry in Tunnelblick.app's Info.plist. It can be overridden by a forced preference (from a Deployed version of Tunnelblick) named "IPCheckURL". For security reasons, it must be a forced preference.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS