

&lt;hr&gt;


<font size='3'><b><a href='http://code.google.com/p/tunnelblick/downloads/detail?name=Tunnelblick_3.1beta14.dmg'>Download Tunnelblick 3.1beta14</a></b></font>


&lt;hr&gt;



**[Full Release Notes](RlsNotes.md)**

## What's New in Tunnelblick 3.1beta14 (Changes from 3.1beta12) ##
  * <font color='red'><b>IMPORTANT NOTE FOR THOSE USING "WHEN COMPUTER STARTS" WITH EARLIER BETA VERSIONS:</b></font> The first time that you update to Tunnelblick 3.1beta08 or above from 3.1beta02 - 3.1beta06, Tunnelblick will not recognize any **running** "when computer starts" configurations. Five to ten seconds after you start Tunnelblick, they will be identified as unknown OpenVPN processes and you will be given the choice to leave them alone or disconnect them. You should chose to disconnect them in this dialog and then manually connect them in Tunnelblick. (You do not need to do this immediately, but you will not be able to control them with Tunnelblick. The dialog will appear each time you start Tunnelblick if these connections are still active.) This need only be done once, and is not necessary if there are no "when computer starts" configurations that are connected at the time you update.



  * Fixes [Issue 159](https://code.google.com/p/tunnelblick/issues/detail?id=159) problem that, under certain circumstances, crashes client.down.tunnelblick.sh

  * Includes OpenVPN version 2.1.3.

  * Thanks to Mohammad A. Haque: Includes the OpenSSL v. 1.0.0a library imbedded into the included OpenVPN binary. This adds support for the following:

> Digests:<br>
<blockquote>ecdsa-with-SHA1 160 bit digest size<br>
MD2 128 bit digest size<br>
RSA-MD2 128 bit digest size<br>
RSA-SHA224 224 bit digest size<br>
RSA-SHA256 256 bit digest size<br>
RSA-SHA384 384 bit digest size<br>
RSA-SHA512 512 bit digest size<br>
SHA224 224 bit digest size<br>
SHA256 256 bit digest size<br>
SHA384 384 bit digest size<br>
SHA512 512 bit digest size<br>
whirlpool 512 bit digest size<br></blockquote></li></ul>

<blockquote>Ciphers:<br>
<blockquote>CAMELLIA-128-CBC 128 bit default key (fixed)<br>
CAMELLIA-128-CFB 128 bit default key (fixed)<br>
CAMELLIA-128-CFB1 128 bit default key (fixed)<br>
CAMELLIA-128-CFB8 128 bit default key (fixed)<br>
CAMELLIA-128-OFB 128 bit default key (fixed)<br>
CAMELLIA-192-CBC 192 bit default key (fixed)<br>
CAMELLIA-192-CFB 192 bit default key (fixed)<br>
CAMELLIA-192-CFB1 192 bit default key (fixed)<br>
CAMELLIA-192-CFB8 192 bit default key (fixed)<br>
CAMELLIA-192-OFB 192 bit default key (fixed)<br>
CAMELLIA-256-CBC 256 bit default key (fixed)<br>
CAMELLIA-256-CFB 256 bit default key (fixed)<br>
CAMELLIA-256-CFB1 256 bit default key (fixed)<br>
CAMELLIA-256-CFB8 256 bit default key (fixed)<br>
CAMELLIA-256-OFB 256 bit default key (fixed)<br>
DES-EDE3-CFB1 192 bit default key (fixed)<br>
DES-EDE3-CFB8 192 bit default key (fixed)<br>
IDEA-CBC 128 bit default key (fixed)<br>
IDEA-CFB 128 bit default key (fixed)<br>
IDEA-OFB 128 bit default key (fixed)<br>
RC5-CBC 128 bit default key (variable)<br>
RC5-CFB 128 bit default key (variable)<br>
RC5-OFB 128 bit default key (variable)<br>
SEED-CBC 128 bit default key (fixed)<br>
SEED-CFB 128 bit default key (fixed)<br>
SEED-OFB 128 bit default key (fixed)<br></blockquote></blockquote>

<blockquote>TLS Ciphers:<br>
<blockquote>CAMELLIA128-SHA<br>
CAMELLIA256-SHA<br>
DHE-DSS-CAMELLIA128-SHA<br>
DHE-DSS-CAMELLIA256-SHA<br>
DHE-DSS-SEED-SHA<br>
DHE-RSA-CAMELLIA128-SHA<br>
DHE-RSA-CAMELLIA256-SHA<br>
DHE-RSA-SEED-SHA<br>
ECDH-ECDSA-AES128-SHA<br>
ECDH-ECDSA-AES256-SHA<br>
ECDH-ECDSA-DES-CBC3-SHA<br>
ECDH-ECDSA-RC4-SHA<br>
ECDH-RSA-AES128-SHA<br>
ECDH-RSA-AES256-SHA<br>
ECDH-RSA-DES-CBC3-SHA<br>
ECDH-RSA-RC4-SHA<br>
ECDHE-ECDSA-AES128-SHA<br>
ECDHE-ECDSA-AES256-SHA<br>
ECDHE-ECDSA-DES-CBC3-SHA<br>
ECDHE-ECDSA-RC4-SHA<br>
ECDHE-RSA-AES128-SHA<br>
ECDHE-RSA-AES256-SHA<br>
ECDHE-RSA-DES-CBC3-SHA<br>
ECDHE-RSA-RC4-SHA<br>
IDEA-CBC-SHA<br>
PSK-3DES-EDE-CBC-SHA<br>
PSK-AES128-CBC-SHA<br>
PSK-AES256-CBC-SHA<br>
PSK-RC4-SHA<br>
SEED-SHA<br></blockquote></blockquote>

<blockquote>For a complete list of available digests, ciphers, and TLS ciphers, type the following into Terminal:<br>
<pre><code>    sudo ./openvpn --show-digests --show-ciphers --show-tls<br>
</code></pre></blockquote>

<blockquote>("sudo" is needed if Tunnelblick.app has been run at least once, because Tunnelblick secures the OpenVPN binary by making it owned and executable only by root.)</blockquote>

<hr />

<h3>PLEASE USE THE <a href='http://groups.google.com/group/tunnelblick-discuss'>TUNNELBLICK DISCUSSION GROUP</a> FOR COMMENTS OR QUESTIONS