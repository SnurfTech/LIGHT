# LIGHT
LIGHT stands for Logical Integrity Guarantee for Honest Transmission. It is like an alternative for GnuPG. It allows you too generate a private and public key, use the private key to sign files, and use the public key to verify the signatures of the files.

There are three scripts -- one to generate keys, one to sign files, and one to verify those files with their signatures.

## LIGHT-genkey
Usage: ```light-genkey <FLAGS & OPTIONS>``` (I'm not putting much information on how to use this command, as code can change and I'm too lazy to update this page a lot. For example, the help page. Run ```light-genkey --help``` to actually view help and usage information.)

## LIGHT-sign
Usage: ```light-sign <FLAGS & OPTIONS>``` (I'm not putting much information on how to use this command, as code can change and I'm too lazy to update this page a lot. For example, the help page. Run ```light-sign --help``` to actually view help and usage information.)

## LIGHT-verify
Usage: ```light-verify <FLAGS & OPTIONS>``` (I'm not putting much information on how to use this command, as code can change and I'm too lazy to update this page a lot. For example, the help page. Run ```light-verify --help``` to actually view help and usage information.)

## How to Install (Automatically)
Just use your Linux distribution's package manager! LIGHT may be there, or it may not. If it is not, see How to Install (Manually).

## How to Install (Manually)
### Dependencies
> If for whatever reason you do not have Coreutils, BusyBox will also work.
```
openssl
coreutils
bash
curl
```
> Bash is the interpreter for the scripts.
 
> Coreutils is used for -- well -- running stuff like cat and [?

> OpenSSL is used for generating keys, generating signatures, and verifing signatures.

> Curl is used for downloading the files needed to run LIGHT. This can be removed later if you do not need it anymore.

### Download the scripts and put them in a folder in your PATH environment variable
```
mkdir -p ~/.local/bin
curl -L https://github.com/SnurfTech/LIGHT/raw/refs/heads/main/light-genkey -o ~/.local/bin/light-genkey
chmod +x ~/.local/bin/light-genkey
curl -L https://github.com/SnurfTech/LIGHT/raw/refs/heads/main/light-sign -o ~/.local/bin/light-sign
chmod +x ~/.local/bin/light-sign
curl -L https://github.com/SnurfTech/LIGHT/raw/refs/heads/main/light-verify -o ~/.local/bin/light-verify
chmod +x ~/.local/bin/light-verify
```
Now, add ```~/.local/bin``` to your PATH environment variable if it is not already there.
```
echo 'export PATH=$PATH:~/.local/bin' >> ~/.profile
```

> If you want, you can replace ```~/.profile``` with something like ```~/.bashrc```.
