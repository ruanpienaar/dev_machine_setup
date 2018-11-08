# Mac Mojave Setup

* Install Xcode by hand

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