# LIGHT
LIGHT stands for Logical Integrity Guarantee for Honest Transmission. It allows you too generate a private and public key, use the private key to sign files, and use the public key to verify the signatures of the files.

There are three scripts -- one to generate keys, one to sign files, and one to verify those files with their signatures.

## LIGHT-genkey
Usage: ```light-genkey <FLAGS & OPTIONS>``` (I'm not putting much information on how to use this command, as code can change and I'm too lazy to update this page a lot. For example, the help page. Run ```light-genkey --help``` to actually view help and usage information.)

## LIGHT-sign
Usage: ```light-sign <FLAGS & OPTIONS>``` (I'm not putting much information on how to use this command, as code can change and I'm too lazy to update this page a lot. For example, the help page. Run ```light-sign --help``` to actually view help and usage information.)

## LIGHT-verify
Usage: ```light-verify <FLAGS & OPTIONS>``` (I'm not putting much information on how to use this command, as code can change and I'm too lazy to update this page a lot. For example, the help page. Run ```light-verify --help``` to actually view help and usage information.)

## How to Install (Manually)
### Dependencies
> If for whatever reason you do not have Coreutils, BusyBox will also work.
```
openssl
coreutils
bash
```
> Bash is the interpreter for the scripts.
 
> Coreutils is used for -- well -- running stuff like cat and [?

> OpenSSL is used for generating keys, generating signatures, and verifing signatures.

### Download the scripts and put them in a folder in your PATH environment variable
```
curl -L https
