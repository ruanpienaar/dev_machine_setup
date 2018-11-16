# Mac Mojave Setup

Install Xcode

sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

Create a .zprofile file, so all shells will be interactive ( used by Ansible )

# include .zshrc if it exists
if [ -f "$HOME/.zshrc" ]; then
  . "$HOME/.zshrc"
fi

And add the following to your .zshrc:
# Leaving this here for Ansible - since the ssh command non-interactive shell
# Does not set PATH

export PATH="/usr/local/bin:$PATH"

( So that you can do "source $USER/.zshrc && STUFF  in  ansible )

Before Ansible

sudo easy_install pip
OR 
sudo curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py

sudo pip install ansible

Java
https://www.oracle.com/technetwork/java/javase/downloads/index.html

Ansible

roles need to install first:
ansible-galaxy install geerlingguy.homebrew

Setup my common packages:
git clone https://github.com/ruanpienaar/dev_machine_setup
cd dev_machine_setup/mac/mojave/
( joe, ack ) ( i know homebrew never requires sudo, but the role from geerlingguy.homebrew needs it ... )
ansible-playbook --ask-become-pass homebrew_and_default_dev_packages.yml

setup localhost
sudo echo "localhost ansible_user=$USER" > /etc/ansible/hosts

#Erlang
git clone https://github.com/ruanpienaar/Erlang_ansible_kerl
cd Erlang_ansible_kerl
ansible-playbook --ask-become-pass erlang_homebrow_deps_packages.yml

Fix the openssl homebrew: ( homebrew does not want to link over the mac openssl )
```
echo 'export PATH="/usr/local/opt/openssl/bin:$PATH"' >> ~/.zshrc
```

ansible-playbook --ask-become-pass kerl.yml
ansible-playbook kerl_build_install_erlang.yml

Erlang Notes: ( KERL options set in kerl_build_install_erlang.yml )
./configure --with-ssl=/usr/local/opt/openssl

( sourcing RC file in yml file steps, since the ssh command way of doing things in ansbile, starts a non-interactive shell that 
  does not load a full/correct environment, and hence RC files are not loaded )
check "kerl_build_install_erlang.yml" for install folder, locate "activate" and source activate in RC file

Rebar3:
git clone https://github.com/ruanpienaar/dev_machine_setup
cd dev_machine_setup/ansible
ansible-playbook rebar3.yml
export PATH=$HOME/.cache/rebar3/bin:$PATH


SSH Keys
https://blog.g3rt.nl/upgrade-your-ssh-keys.html
ssh-keygen -o -a 100 -t ed25519    ( Use a damn passphrase ... )
eval "$(ssh-agent -s)"
ssh-add -K ~/.ssh/id_ed25519

If you fancy not having to type in your passphrase for your key:
ssh-keygen -p


# Apps
## Editors
### Sublime
* https://www.sublimetext.com/3
* install Package Control
* Open User Settings, and take contents from sublime_text_3/
* Sublime packages to install:
** AdvancedNewFile
** SpaceGray theme

### joe
brew install joe
```
joe ~/.joerc
```
```
:include /usr/local/etc/joe/joerc
-nobackups
```

## Documentation
### Dashdoc
https://kapeli.com/dash

## Productivity
### Zonebox
https://itunes.apple.com/gb/app/zonebox/id597870795?mt=12

# Command Line
## Shell
### Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"


Command Line setup

* locate
** sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist

* python pip
** sudo curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && sudo python get-pip.py









