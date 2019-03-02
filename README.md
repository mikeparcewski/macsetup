# MacOS Development Setup

Goal is to quickly set up a fresh install (or existing install) with base set of tools.

1. Install homebrew
  ```
  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  ```
2. Download the Homebrew bundle
  ```
  curl -O https://raw.githubusercontent.com/mikeparcewski/macsetup/master/Brewfile
  ```
3. Load the brew bundle
  ```
  brew bundle
  ```
4. Install oh-my-zsh
  ```
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
  ```
5. Configure jenv - http://www.jenv.be/
    * Create config directory
    ```
    mkdir -p ~/.jenv/versions
    ```
    * Update .zshrc with some jenv stuff
    ```
    echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.zshrc
    echo 'eval "$(jenv init -)"' >> ~/.zshrc
    source ~/.zshrc
    ``` 
    * Set up the JDK's for jenv     
    ```
    for i in `ls -d -1 "/Library/Java/JavaVirtualMachines/"*/Contents/Home`; do jenv add $i; done
    ```
    * Enable all the plugins for jenv
    ```
    for i in `jenv plugins`; do if [ "" != $i ]; then jenv enable-plugin $i; fi; done
    ```
    > Check out http://www.jenv.be, and skip the "installation" sections and jump straight to "configure" and "And Use!" sections.
8. Clean up the dock (e.g. add/remove any programs needed)

## Other useful hacks
To add a space to between items in the dock, just run the below command.  After you'll see an empty space at the end of the bar and you can just drag in between your apps
```
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}'; killall Dock
```
