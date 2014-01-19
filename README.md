# ooo-bulb #
---

A standalone wifi enabled light bulb that shows in/out of office status

## Notes ##
1. YouTube video outlining how to create a certificate request on Windows [https://www.youtube.com/watch?v=mpzSXAW0qUI](https://www.youtube.com/watch?v=mpzSXAW0qUI)
2. cnf error [http://jaspreetchahal.org/warning-cant-open-config-file-usrlocalsslopenssl-cnf/](http://jaspreetchahal.org/warning-cant-open-config-file-usrlocalsslopenssl-cnf/)
3. Article outlining how to create a .p12 file from the PEM file in note #1 [http://help.adobe.com/en_US/as3/iphone/WS144092a96ffef7cc-371badff126abc17b1f-7fff.html](http://help.adobe.com/en_US/as3/iphone/WS144092a96ffef7cc-371badff126abc17b1f-7fff.html)
4. Untested steps to automate the above:
<pre>@echo off
set OPENSSL_CONF=c:\OpenSSL-Win32\bin\openssl.cfg
openssl genrsa -out mykey.key 2048
openssl -new -key mykey.key -out CertificateSigningRequest -subj "/emailAddress=troy.forster@gmail.com, CN=Troy Forster, C=CA"
@echo submit the certificate request to https://developer.apple.com/account/ios/certificate/certificateCreate.action and download the resulting .cer file to this working folder & pause
openssl x509 -in developer_identity.cer -inform DER -out developer_identity.pem -outform PEM
openssl pkcs12 -export -inkey mykey.key -in developer_identity.pem -out iphone_dev.p12</pre>
5.&nbsp;Create a provisioning profile [https://developer.apple.com/account/ios/profile/profileList.action](https://developer.apple.com/account/ios/profile/profileList.action)
