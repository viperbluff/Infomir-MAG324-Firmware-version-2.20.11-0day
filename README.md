# Infomir-MAG324-Firmware-version-2.20.11-0day
Vulnerability Details about Infomir MAG324 IPTV STB 0day 

Please find the brief description about the finding below:

Title: DropBear Private ssh key Disclosure
Severity:HIgH
Target: Infomir Mag324 2.20.11 release

Vulnerability Description: Dropbear is an alternative to OpenSSH which can be used for remotely logging into machines either using Username/password or Public/Private Key combination.If private keys are accessible a malicious user can use them to remotely access IPTV STB using Public key authentication mechanism by default on port 22.

Observation:

Assessor observed that Dropbear SSH DSS/RSA private keys were accessible in the /etc/dropbear folder stored in the firmware filesystem. Firmware file system was downloaded from here: https://soft.infomir.com/mag324/release/2.20.11/ .
As it's publicly known that dropbear doesn't work on encrypted private files so these private keys could be used to remotely take over thousands of Infomir MAG324 IPTV boxes by using the Public key SSH authentication mechanism.

These RSA/DSS private keys can be used to remotely access MAG324 IPTV STB using below command:

dbclient root@MAG324_STB_IP -i /etc/dropbear/dropbear_rsa_host_key 

where dropbear_rsa_host_key is the private key which an attacker can easily obtain from the /etc/dropbear folder.

Steps To Reproduce:

1. Go to https://soft.infomir.com/mag324/release/2.20.11/
2. Download rootfs-2.20.11.tgz compressed archive containing the firmware filesystem
3. Go to /etc/dropbear directory 
4. Access to Dropbear Private keys.


Note:Vulnerability Reported to Infomir , no action has been taken from their end.


