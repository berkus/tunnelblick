**HOW TO DIGITALLY SIGN THE TUNNELBLICK APPLICATION**

_Note: This page describes how to digitally sign the Tunnelblick application or a rebranded version. Please read [Digital Signatures](cDigitalSignatures.md)_ for background on Tunnelblick's use of digital signatures.

## WHAT YOU NEED ##

To digitally sign the application (Tunnelblick or a rebranded version), you need:
  * OS X 10.9.4 ("Mavericks") or higher;
  * A copy of the unsigned application;
  * A code signing certificate; and
  * The signing script (below).

You cannot use Xcode to sign Tunnelblick because you must **_build_** it on OS X 10.6.8 with Xcode 3.2.2 which doesn't do signatures, but **_sign_** it on OS X 10.9.4 ("Mavericks") or higher. You don't need Xcode to sign it

### OS X 10.9.4 ("Mavericks") or Higher ###
You need Mac OS X 10.9.4 ("Mavericks") because OS X 10.10 ("Yosemite") requires applications to be signed using OS X 10.9.4 or higher. Although Tunnelblick must be **_built_** on OS X 10.6.8 with Xcode 3.2.2, it must be **_signed_** on OS X 10.9.4 ("Mavericks") or higher.

### Unsigned Application ###
To get an unsigned version of Tunnelblick or your rebranded version, build an "Unsigned Release" of the source code using the instructions at [Building From Source](https://code.google.com/p/tunnelblick/wiki/cBuild).

### Code signing Certificate ###
The code signing certificate can be a "self-signed" certificate or a certificate from Apple. There is one difference: if you use a self-signed certificate, Gatekeeper in OS X 10.8 ("Mountain Lion") and higher may not allow the first run of the self-signed application by double-clicking it. The user will need to Control-click or right-click and select "Open". That is because the Gatekeeper default is to allow the first launch of an application only if it is signed by an Apple-recognized developer.

To get a self-signed code signing certificate, use the OS X Keychain Assistant application. Apple used to have instructions on doing this but they have disappeared. They may be accessed from the Internet Archive using [this link](http://web.archive.org/web/20090119080759/http://developer.apple.com/documentation/Security/Conceptual/CodeSigningGuide/Procedures/chapter_3_section_2.html),

To get an certificate from Apple, you must be an [Apple Developer](https://developer.apple.com). Request your Apple certificate and install it into your Keychain. You can do this from a recent version of Xcode running on OS X 10.9 ("Mavericks") or higher.

To sign the kexts, your certificate must be a "kext-signing" certificate. If you do not have one and Apple will not give you one, you can just copy the two signed kexts from a recent version of Tunnelblick; they are signed with a "kext-signing" certificate.

## SIGNING SCRIPT ##

Use following script to sign Tunnelblick or a rebranded version of Tunnelblick. The command line is:

```
 ./script-name        app-path     certificate-name
```

Notes:
  1. _Be sure the script has "Unix" line endings -- OS X chokes on Windows line endings in bash scripts. You can use the excellent freeware [ConvertNewLines program](https://lionel.kr.hs-niederrhein.de//~dalitz/data/software/macosx/#tools) to force Unix line endings._
  1. _Be sure to "chmod +x" the script before attempting to execute it._
  1. _If you get error messages that "Agreeing to the Xcode/iOS license requires admin privileges, please re-run as root via sudo.", type the following into Terminal:
```
      sudo codesign
```
> before running the script._

```
#!/bin/bash
#
# sign-tunnelblick
#
# A script to digitally sign Tunnelblick.app or a rebranded version of Tunnelblick.app
#
# Version 2, 2014-09-19
#     * Does not require "designated requirements"
#     * Requires OS X 10.9.4 or higher (because 10.9.5 and higher require signatures generated on 10.9.4 or later)
#     * Is more "robust" with more error checking and progress indications

readonly app_path="$1"
readonly certificate_name="$2"
readonly this_script_name="`basename "$0"`"

if [ "${app_path}" == "" -o "${certificate_name}" == "" ] ; then
  echo "Usage:"
  echo "     ./${this_script_name}    application_path    certificate_name"
  exit 1
fi

if [ -d "${app_path}/Contents/_CodeSignature" ] ; then
  echo "${app_path} has already been signed"
  exit 1
fi

# Check that this script is running on OS X 10.9.4 or higher because only 10.9.4 or higher can sign kexts for 10.9.5 or higher
readonly os_x_version="`sw_vers -productVersion`"
readonly os_x_major="${os_x_version%%.*}"
readonly os_x_minor_debug="${os_x_version#*.}"
readonly os_x_minor="${os_x_minor_debug%%.*}"
readonly os_x_debug="${os_x_minor_debug#*.}"
if [ ${os_x_major} -lt 10 ] ; then
  echo "Error: This script must be run on OS X 10.9.4 or later because only 10.9.4 or higher can sign kexts for 10.9.5 or higher (running on ${os_x_major}.${os_x_minor}.${os_x_debug})"
  exit 1
fi
if [ ${os_x_major} -eq 10 ] ; then
  if [ ${os_x_minor} -lt 9 ] ; then
    echo "Error: This script must be run on OS X 10.9.4 or later because only 10.9.4 or higher can sign kexts for 10.9.5 or higher (running on ${os_x_major}.${os_x_minor}.${os_x_debug})"
    exit 1
  fi
  if [ ${os_x_minor} -eq 9 ] ; then
    if [ ${os_x_debug} -lt 4 ] ; then
      echo "Error: This script must be run on OS X 10.9.4 or later because only 10.9.4 or higher can sign kexts for 10.9.5 or higher (running on ${os_x_major}.${os_x_minor}.${os_x_debug})"
      exit 1
    fi
  fi
fi


# Remove ' Unsigned' from the application's Info.plist
sed -e "s| Unsigned||g" "${app_path}/Contents/Info.plist" > temp.plist
cp -f temp.plist "${app_path}/Contents/Info.plist"
rm temp.plist

echo "Signing helpers..."

codesign -s "${certificate_name}"    "${app_path}/Contents/Resources/atsystemstart"
codesign -s "${certificate_name}"    "${app_path}/Contents/Resources/installer"
codesign -s "${certificate_name}"    "${app_path}/Contents/Resources/openvpnstart"
codesign -s "${certificate_name}"    "${app_path}/Contents/Resources/process-network-changes"
codesign -s "${certificate_name}"    "${app_path}/Contents/Resources/standardize-scutil-output"

echo "Signing tun and tap kexts..."

readonly signed_tun_path="${app_path}/Contents/Resources/tun-signed.kext"
readonly signed_tap_path="${app_path}/Contents/Resources/tap-signed.kext"

# Before signing each of the signed tun & tap kexts, remove ' Unsigned' from its Info.plist
readonly signed_tun_plist_path="${signed_tun_path}/Contents/Info.plist"
readonly signed_tap_plist_path="${signed_tap_path}/Contents/Info.plist"
sed -e "s| Unsigned||g" "${signed_tun_plist_path}" > temp_tun.plist
sed -e "s| Unsigned||g" "${signed_tap_plist_path}" > temp_tap.plist
cp -f temp_tun.plist "${signed_tun_plist_path}"
cp -f temp_tap.plist "${signed_tap_plist_path}"
rm -f temp_tun.plist temp_tap.plist

# Sign the _signed_ tun and tap kexts (but don't sign the other tun and tap kexts -- they _cannot_ be signed)
codesign -s "${certificate_name}"    "${signed_tun_path}"
codesign -s "${certificate_name}"    "${signed_tap_path}"

# Sign the openvpn and openvpn-down-root.so binaries
for d in `ls "${app_path}/Contents/Resources/openvpn"`
do
  if [ "${d}" != "default" ] ; then
    codesign -s "${certificate_name}"    "${app_path}/Contents/Resources/openvpn/${d}/openvpn"
    codesign -s "${certificate_name}"    "${app_path}/Contents/Resources/openvpn/${d}/openvpn-down-root.so"
  fi
done

echo "Signing Sparkle framework..."

codesign -s "${certificate_name}"    "${app_path}/Contents/Frameworks/Sparkle.framework/Versions/A"

echo "Signing the application..."

codesign -s "${certificate_name}"    "${app_path}"

echo "Done. The application has been digitally signed."

```

Note that this assumes you have a "kext-signing" certificate; if you don't, modify the script to copy the "tun-signed.kext" and "tap-signed.kext" from a recent copy of Tunnelblick into your rebranded application.

---


### PLEASE USE THE [TUNNELBLICK DISCUSSION GROUP](https://groups.google.com/forum/#!forum/tunnelblick-discuss) FOR COMMENTS OR QUESTIONS