# LIGHT
LIGHT stands for Logical Integrity Guarantee for Honest Transmission. It is like an alternative for GnuPG. It allows you too generate a private and public key, use the private key to sign files, and use the public key to verify the signatures of the files.

There are three scripts -- one to generate keys, one to sign files, and one to verify those files with their signatures.

## Table of Contents
- [Usages & Help](#usages--help)
  - [LIGHT-genkey](#light-genkey)
  - [LIGHT-sign](#light-sign)
  - [LIGHT-verify](#light-verify)
- [Installing (Manually)](#installing-manually)
  - [Dependencies](#dependencies)
  - [Downloading the scripts and putting them in a folder in your PATH environment variable](#downloading-the-scripts-and-putting-them-in-a-folder-in-your-path-environment-variable)
- [Uninstalling (Manually)](#uninstalling-manually)
  - [Deleting the scripts](]#deleting-the-scripts)
  - [(OPTIONAL) Removing extra configurations](#optional-removing-extra-configurations)
  - [(OPTIONAL) Cleaning up](#optional-cleaning-up)

## Usages & Help
### LIGHT-genkey
Usage: ```light-genkey <FLAGS & OPTIONS>``` (I'm not putting much information on how to use this command, as code can change and I'm too lazy to update this page a lot. For example, the help page. Run ```light-genkey --help``` to actually view help and usage information.)

### LIGHT-sign
Usage: ```light-sign <FLAGS & OPTIONS>``` (I'm not putting much information on how to use this command, as code can change and I'm too lazy to update this page a lot. For example, the help page. Run ```light-sign --help``` to actually view help and usage information.)

### LIGHT-verify
Usage: ```light-verify <FLAGS & OPTIONS>``` (I'm not putting much information on how to use this command, as code can change and I'm too lazy to update this page a lot. For example, the help page can change. So just run ```light-verify --help``` to actually view help and usage information.)

## Installing (Manually)
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

### Downloading the scripts and putting them in a folder in your PATH environment variable
First, download the scripts.
```
mkdir -p ~/.local/bin
curl -L https://github.com/SnurfTech/LIGHT/raw/refs/heads/main/light-genkey -o ~/.local/bin/light-genkey
chmod +x ~/.local/bin/light-genkey
curl -L https://github.com/SnurfTech/LIGHT/raw/refs/heads/main/light-sign -o ~/.local/bin/light-sign
chmod +x ~/.local/bin/light-sign
curl -L https://github.com/SnurfTech/LIGHT/raw/refs/heads/main/light-verify -o ~/.local/bin/light-verify
chmod +x ~/.local/bin/light-verify
```
Now, add ```~/.local/bin``` to your PATH environment variable permanently if it is not already there.
```
echo 'export PATH=$PATH:~/.local/bin' >> ~/.bashrc
```
Now, add ```~/.local/bin``` to your temporary PATH environment variable so that you don't need to restart your shell for changes to be placed.
```
export PATH=$PATH:~/.local/bin
```
If for whatever reason ```~/.bashrc``` is not being sourced at shell startup, you can run this.
```
cat << EOF >> ~/.bash_profile
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
EOF
```

> If you want, you can replace ```~/.bash_profile``` with something else that is ran or sourced at shell startup.

> Also if you want, for all of these steps, you can replace ```~/.bashrc``` with something like ```~/.profile```.

## Uninstalling (Manually)
### Deleting the scripts
Delete the scripts.
```
rm -f ~/.local/bin/light-genkey ~/.local/bin/light-sign ~/.local/bin/light-verify
```

### (OPTIONAL) Removing extra configurations
> You could be using some of these configurations for other things. That is why every step for removing extra configurations is optional. (Eg. You might have programs other than LIGHT in ```~/.local/bin``` that you still need in your PATH.)

Remove ```~/.local/bin``` from PATH
```
sed -i "/export PATH=\$PATH:~\/\.local\/bin$/d" ~/.bashrc
```
> If you used something like ```~/.profile``` instead of ```~/.bashrc``` to install LIGHT, then just replace ```~/.bashrc``` with ```~/.profile``` or whatever you used instead.

Remove ```~/.bashrc``` from being automatically sourced.
> Only run this if you went through the installation step that made ```~/.bashrc``` get sourced automatically on shell startup. If it was already getting sourced, then it is recommended to not run this uninstallation step. (This also still applies if you used something like ```~/.profile``` instead of ```~/.bashrc```.)

```
sed -i '/^if \[ -f ~\/\.bashrc \]; then$/{
N
N
/if \[ -f ~\/\.bashrc \]; then\n    source ~\/\.bashrc\nfi/d
}' ~/.bash_profile
```
> If you used something other than ```~/.bash_profile``` to install LIGHT, then just replace ```~/.bash_profile``` with whatever you used instead.

### (OPTIONAL) Cleaning up
> You could be using some of these things we are going to clean up for other things. This is why every step for cleaning up is optional. (Eg. You might have programs other than LIGHT in ```~/.local/bin``` that you still need.)

Remove ```~/.local/bin```
```
rmdir --ignore-fail-on-non-empty -p ~/.local/bin
rmdir --ignore-fail-on-non-empty -p ~/.local
```
> The first command will fail if ```~/.local/bin``` is not empty. LIGHT will probably not be in there (assuming you ran the other non-optional uninstallation steps), but other programs might. The first command will fail if that is true. This is to make sure you don't lose anything important that might still be inside ```~/.local/bin```. Also, the second command will fail as well if the first command does. If the first command fails but you still really want to delete ```~/.local/bin```, then run ```rm -rf ~/.local/bin```.

> The second command will fail if ```~/.local``` is not empty. If this happens, this could I either mean the first command failed, or there are other folders in ```~/.local```. (Eg. ```~/.local/share```.) This is to make sure that you don't lose anything important that might still be inside ```~/.local```. If the second command fails but you still really want to delete ```~/.local```, then run ```rm -rf ~/.local```.
