To intercept the tarfic on Android App with Burpsuite you should follow those steps
# 1 Installing Burpsuite Certificate
The certificate should be in the DER format 

![image](https://github.com/user-attachments/assets/0a596dfe-1208-4669-b66a-fdda1d5649d9)

# 2 Converting BurpSuites Certificate With OpenSSL
```Bash
PS C:\Users\cat\Desktop> openssl x509 -inform DER -in .\portswigger2025.crt -out burp.pem
PS C:\Users\cat\Desktop> openssl x509 -inform PEM -subject_hash_old -in .\burp.pem
9a5ba575
-----BEGIN CERTIFICATE-----
MIIDqDCCApCgAwIBAgIFANXhiY0wDQYJKoZIhvcNAQELBQAwgYoxFDASBgNVBAYT
....
TmHQEIpzsJB7hFU6+/8b8emw8L/4CLw8vFOdHjmklyzAZvQhQdWBPF/27qYIc19W
SrLDsfJeHoModtOLnxh1Gu41evq4+b1kOTQFrg==
-----END CERTIFICATE-----
PS C:\Users\cat\Desktop> mv .\burp.pem 9a5ba575.0
```
# 3 Pushing The Certificate Into The Device
```Bash
adb root
adb remount
adb push 9a5ba575.0 /system/etc/security/cacerts
```
# 4 Changing Permissions For Certificate 
```bash
adb shell
/ # cd system/etc/security/cacerts
/system/etc/security/cacerts/ # chmod 644 9a5ba575.0
```
# 5 Setting Proxy With ADB
```bash
adb shell settings put global http_proxy <IPv4_addr>:8080
```
# 6 Making Proxy Listeners  On All Interfaces

![image](https://github.com/user-attachments/assets/2c97a090-6989-4890-a594-568f96cf7fbd)







