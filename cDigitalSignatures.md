<font color='red'>Most Tunnelblick users do not need to use the information on this page. This page is primarily for those who create <a href='cCusDeployed.md'>Deployed</a> versions of Tunnelblick._</font>_

## Digital Signatures ##
Tunnelblick uses two different types of digital signatures:
  * **Application signature** Tunnelblick.app may be digitally signed by the Tunnelblick Project with the Project's OS X digital signature. The signature is used in OS X 10.5 ("Leopard") and higher to allow an updated application with the same signature as the original application to access Keychain items created by the original application without OS X prompting the user for permission.
  * **Update signature** Updates to Tunnelblick are always digitally signed by the Tunnelblick Project. This is part of the update process, to ensure that updates to Tunnelblick are genuine and have not been tampered with or corrupted.

## Why Application Signatures Are Useful ##
If the user agrees, Tunnelblick stores usernames, passwords and passphrases for VPNs in the user's Keychain so that the user does not have to enter them each time a connection is made.

For security reasons, OS X is careful when applications access the user's Keychain. Usually only the original application that created a Keychain item is allowed access to it. This means that when an application is updated, even though it has the same name, OS X will recognize that it is different and ask the user if the program may access the Keychain. In OS X 10.5 and higher, if the updated application is "digitally signed" by the same signer as the original application, OS X will allow it to access the Keychain without asking the user.

Digital signatures are also used by the Gatekeeper on OS X 10.8 ("Mountain Lion") and higher. By default, Gatekeeper allows the installation only of applications signed by developers recognized by Apple. Signed versions of Tunnelblick versions 3.3beta08 and higher are signed by such a developer so that they may be installed easily.

## How Application Signatures Can Cause Problems for Deployed Versions of Tunnelblick ##
If an application is digitally signed, and a change is made to the application, the signature becomes invalid. That can cause problems for [Deployed](cCusDeployed.md) versions of Tunnelblick, because the process of creating a Deployed version involves changing the application by adding a folder inside the application itself. If such a folder is added to a signed version of Tunnelblick, the signature becomes invalid. OS X 10.8 and higher will not allow the user to install Tunnelblick, and OS X 10.5 and higher will refuse the program access to it's Keychain items, without asking the user.

The way to solve this problem is to add the folder to an _unsigned_ version of Tunnelblick,  then sign the unsigned, already modified Tunnelblick. That will give users the benefits of digital signatures. See [Signing Tunnelblick](cSigningTunnelblick.md) for details on how to digitally sign Tunnelblick or a rebranded version of Tunnelblick.

## Update Signatures ##
Whenever Tunnelblick is updated by the built-in update process, the update itself will only be digitally signed under certain circumstances.
  * Standard Tunnelblick versions before 3.2beta34 will be updated with signed versions; and
  * Standard Tunnelblick versions 3.2beta34 and higher will be updated with signed versions only if they are themselves signed, otherwise they are updated with unsigned versions.
  * Standard Tunnelblick versions 3.2.3 and higher will be updated with signed versions unless they are [Deployed](cCusDeployed.md) versions, or there is a problem with the digital signature.
  * "Standard" means containing an Info.plist SUFeedURL entry of "http://tunnelblick.net/appcast.rss"
This behavior is meant to be backward compatible for most users of Tunnelblick.

Tunnelblick versions 3.2beta12 (2011-05-16) and higher are digitally signed, so updates to them that are signed will not require the user's permission to access the Keychain.

If an earlier version (for example, 3.1.7) is replaced by a signed version, OS X will ask the user to allow the  new version to access Keychain items. But after that, further replacements by signed versions will be replacing a signed version with another version signed by the same signer (the Tunnelblick Project), and so will OS X will allow access without asking the user.


---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS