<font size='4'>AppleScript Support</font><br>

<br>
<br>
This document is about AppleScript Support -- making Tunnelblick do things via scripting. Tunnelblick itself also uses scripts; see <a href='cUsingScripts.md'>Using Scripts</a>.<br>
<br>
Tunnelblick 3.2beta04 and above may be controlled using AppleScript.<br>
<br>
AppleScripts may connect, disconnect, or list configurations.<br>
<br>
An example of using Tunnelblick's AppleScript support to solve a particular problem is at <a href='https://groups.google.com/d/topic/tunnelblick-discuss/1MDrN6__mdA/discussion'>https://groups.google.com/d/topic/tunnelblick-discuss/1MDrN6__mdA/discussion</a>.<br>
<br>
Please note that the verbs only <i>initiate</i> actions. The "connect" verb, for example, is the equivalent of clicking the "Connect" button. It returns immediately after starting an attempt to connect using a particular configuration and does not indicate the connection has been accomplished successfully.<br>
<br>
<br>
<br>
<hr><br>
<br>
<br>
<br>
<h2>AppleScript Dictionary</h2>

<b><br>
application</b> <i>n</i> :<br>
<br>
<blockquote>contains <i>configurations</i>.</blockquote>

<b><br>
configuration</b> <i>n</i> : A VPN configuration.<br>
<br>
<blockquote>contained by <i>application</i>.</blockquote>

<blockquote>properties</blockquote>

<b><br>
<blockquote>name</b>(text, r/o) : Name of the configuration.</blockquote>

<b><br>
<blockquote>state</b> (text, r/o) : State of the configuration.<br>
<blockquote>'EXITING' means disconnecting or disconnected.<br>
'CONNECTED' means connected.<br>
Other values show progress towards a connection.</blockquote></blockquote>

<b><br>
<blockquote>autoconnect</b> (text, r/o) :<br>
<blockquote>'LAUNCH' means the configuration will be connected automatically when Tunnelblick launches.<br>
'START' means the configuration will be connected automatically when the computer starts.<br>
'NO' means the configuration will not be connected automatically.</blockquote></blockquote>

<b><br>
<blockquote>bytesIn</b> (text, r/o) :<br>
<blockquote>The number of bytes that have come in through the connection since Tunnelblick was launched. (For client configurations only. This will return "0" for configurations that are functioning as a server.)<br>
<blockquote>Available in Tunnelblick 3.3beta02 and later.</blockquote></blockquote></blockquote>

<b><br>
<blockquote>bytesOut</b> (text, r/o) :<br>
<blockquote>The number of bytes that have gone out through the connection since Tunnelblick was launched. (For client configurations only. This will return "0" for configurations that are functioning as a server.)<br>
Available in Tunnelblick 3.3beta02 and later.</blockquote></blockquote>

<b><br>
connect</b><i>v</i> : Connect a VPN configuration.<br>
<br>
<b><br>
<blockquote>connect</b> text : Name of configuration to connect.<br>
<blockquote>→ boolean : Returns true if a connection is being attempted, false if the configuration is already connected.</blockquote></blockquote>

<b><br>
disconnect</b><i>v</i> : Disconnect a VPN configuration.<br>
<br>
<b><br>
<blockquote>disconnect</b> text : Name of configuration to disconnect.<br>
<blockquote>→ boolean : Returns true if a disconnection is being attempted, false if the configuration is already disconnected.</blockquote></blockquote>

<b><br>
connect all</b><i>v</i> : Connect all unconnected VPN configurations.<br>
<br>
<b><br>
<blockquote>connect all</b>
<blockquote>→ integer : Returns the number of configurations for which a connection is being attempted.</blockquote></blockquote>

<b><br>
disconnect all</b><i>v</i> : Disconnect all connected VPN configurations.<br>
<br>
<b><br>
<blockquote>disconnect all</b>
<blockquote>→ integer : Returns the number of configurations for which a disconnection is being attempted.</blockquote></blockquote>

<b><br>
disconnect all except when computer starts</b> <i>v</i> : Disconnect all connected VPN configurations except 'when computer starts' configurations.<br>
<br>
<b><br>
<blockquote>disconnect all except when computer starts</b>
<blockquote>→ integer : Returns the number of configurations for which a disconnection is being attempted.</blockquote></blockquote>

<br>
<br>
<hr><br>
<br>
<br>
<br>
<h2>Examples</h2>

tell application "Tunnelblick"<br>
<br>
<blockquote>get configurations<br>
<blockquote>--> {configuration "Work", configuration "Work-Development", configuration "Home", configuration "Test"}</blockquote></blockquote>

<blockquote>disconnect all<br>
<blockquote>--> 0</blockquote></blockquote>

<blockquote>connect "Work-Development"<br>
<blockquote>--> true</blockquote></blockquote>

<blockquote>disconnect (get name of second configuration)<br>
<blockquote>get name of configuration 2<br>
<blockquote>--> "Work-Development"<br>
</blockquote>disconnect "Work-Development"<br>
<blockquote>--> true</blockquote></blockquote></blockquote>

<blockquote>connect (get name of first configuration where state = "EXITING")<br>
<blockquote>get name of configuration 1 whose state = "EXITING"<br>
<blockquote>--> "Work"<br>
</blockquote>connect "Work"<br>
<blockquote>--> true</blockquote></blockquote></blockquote>

<blockquote>disconnect all except when computer starts<br>
<blockquote>--> 1</blockquote></blockquote>

<blockquote>get state of second configuration<br>
<blockquote>--> "EXITING"</blockquote></blockquote>

<blockquote>get state of first configuration where name = "Work"<br>
<blockquote>--> "EXITING"</blockquote></blockquote>

<blockquote>get name of configurations<br>
<blockquote>--> {"Work", "Work-Development", "Home", "Test"}</blockquote></blockquote>

<blockquote>get state of configurations<br>
<blockquote>--> {"EXITING", "EXITING", "EXITING", "EXITING"}</blockquote></blockquote>

<blockquote>get autoconnect of configurations<br>
<blockquote>--> {"NO", "NO", "NO", "NO"}</blockquote></blockquote>

end tell<br>
<br>
<hr />

<h3>PLEASE USE THE <a href='https://groups.google.com/forum/#!forum/tunnelblick-discuss'>TUNNELBLICK DISCUSSION GROUP</a> FOR COMMENTS OR QUESTIONS