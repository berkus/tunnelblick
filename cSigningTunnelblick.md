**HOW TO DIGITALLY SIGN THE TUNNELBLICK APPLICATION**



_Note: This page describes how to digitally sign the Tunnelblick application or a rebranded version. Please read [Digital Signatures](cDigitalSignatures.md)_ before the rest of this page.

## WHAT YOU NEED ##

To digitally sign the application (Tunnelblick or a rebranded version), you need:
  * OS X 10.9 ("Mavericks") or higher;
  * A copy of the unsigned application;
  * A code signing certificate; and
  * An optional "designated requirement" binary.

### OS X 10.9 ("Mavericks") or Higher ###
You need Mac OS X 10.9 ("Mavericks") because OS X 10.10 ("Yosemite") requires applications to be signed using OS X 10.9.

### Unsigned Application ###
To get an unsigned version of Tunnelblick or your rebranded version, build an "Unsigned Release" of the source code using the instructions at [Building From Source](https://code.google.com/p/tunnelblick/wiki/cBuild).

### Code signing Certificate ###
The code signing certificate can be a "self-signed" certificate or a certificate from Apple. There is one difference: if you use a self-signed certificate, Gatekeeper in OS X 10.8 ("Mountain Lion") and higher may not allow the first run of the self-signed application by double-clicking it. The user will need to Control-click or right-click and select "Open". That is because the Gatekeeper default is to allow the first launch of an application only if it is signed by an Apple-recognized developer.

To get a self-signed code signing certificate, use the OS X Keychain Assistant application. Apple used to have instructions on doing this but they have disappeared. They may be accessed from the Internet Archive using [this link](http://web.archive.org/web/20090119080759/http://developer.apple.com/documentation/Security/Conceptual/CodeSigningGuide/Procedures/chapter_3_section_2.html),

To get an certificate from Apple, you must be an [Apple Developer](https://developer.apple.com). Request your Apple certificates and install them into your Keychain. You can do this from Xcode.

### Designated Requirement Binary ###
You can use a "designated requirement binary" to set requirements for how an application is to be signed. For example, you can require that the Info.plist's CFBundleIdentifier be "com.example.foo". Generating this binary can be done in Xcode, consult Apple's documentation. The only catch is that requirements created in some recent versions of Xcode are considered invalid by OS X 10.5 ("Lion") and will cause problems. Tunnelblick uses a signing requirements binary created on an older version of Xcode that does not cause this problem. See [Gatekeeper vs. Leopard: an ongoing tale](http://fetchsoftworks.com/fetch/blog/gatekeeper-vs-leopard-an-ongoing-tale).

## SIGNING SCRIPT ##

Use following script to sign Tunnelblick or a rebranded version of Tunnelblick:

```
#!/bin/bash
#
# sign-tunnelblick
#
# A script to digitally sign Tunnelblick.app or a rebranded version of Tunnelblick.app
#

if [ "$1" == "" ] ; then
  echo "Usage:"
  echo "     sign-tunnelblick    app_path    certificate_name    requirements_path"
  exit 1
fi

app_path="$1"
certificate_name="$2"
requirements_path="$3"

# Sign the helpers
codesign -s "${certificate_name}"    -r "${requirements_path}"    "${app_path}/Contents/Resources/atsystemstart"
codesign -s "${certificate_name}"    -r "${requirements_path}"    "${app_path}/Contents/Resources/installer"
codesign -s "${certificate_name}"    -r "${requirements_path}"    "${app_path}/Contents/Resources/openvpnstart"
codesign -s "${certificate_name}"    -r "${requirements_path}"    "${app_path}/Contents/Resources/process-network-changes"
codesign -s "${certificate_name}"    -r "${requirements_path}"    "${app_path}/Contents/Resources/standardize-scutil-output"

# Before signing each of the signed tun & tap kexts, remove ' Unsigned' from its Info.plist
signed_tun_path="${app_path}/Contents/Resources/tun-signed.kext"
signed_tap_path="${app_path}/Contents/Resources/tap-signed.kext"
tun_path="${app_path}/Contents/Resources/tun.kext"
tap_path="${app_path}/Contents/Resources/tap.kext"
rm -r "${signed_tun_path}"
rm -r "${signed_tap_path}"
sed -e "s| Unsigned||g" "${tun_path}/Contents/Info.plist" > "${signed_tun_path}/Contents/Info.plist"
sed -e "s| Unsigned||g" "${tap_path}/Contents/Info.plist" > "${signed_tap_path}/Contents/Info.plist"

# Sign the _signed_ tun and tap kexts, but don't sign the other tun and tap kexts
codesign -s "${certificate_name}"    -r "${requirements_path}"    "${signed_tun_path}"
codesign -s "${certificate_name}"    -r "${requirements_path}"    "${signed_tap_path}"

# Sign the openvpn and openvpn-down-root.so binaries
for d in `ls "${app_path}/Contents/Resources/openvpn"`
do
  if [ "${d}" != "default" ] ; then
    codesign -s "${certificate_name}"    -r "${requirements_path}"    "${app_path}/Contents/Resources/openvpn/${d}/openvpn"
    codesign -s "${certificate_name}"    -r "${requirements_path}"    "${app_path}/Contents/Resources/openvpn/${d}/openvpn-down-root.so"
  fi
done

# Sign Sparkle
codesign -s "${certificate_name}"    -r "${requirements_path}"    "${app_path}/Contents/Frameworks/Sparkle.framework/Versions/A"

# Sign the application itself
codesign -s "${certificate_name}"    -r "${requirements_path}"    "${app_path}"
```



---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS