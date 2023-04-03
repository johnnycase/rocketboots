---
title: "Fixing Command Not Found in the Mac Terminal"
datePublished: Fri Dec 02 2022 16:38:42 GMT+0000 (Coordinated Universal Time)
cuid: clb6qcxnj000008mj5t1y2d30
slug: fixing-command-not-found-in-the-mac-terminal
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/dfc573f5bcaa46fd3b64c37366193f1e.jpeg
tags: terminal, macos

---

If you have ever installed a new library or language on your mac, you have probably experienced the frustration of receiving “Command Not Found” when trying to use it in the terminal. This is especially challenging for beginners who may wonder what happened when they installed it in the first place! The good news is, the framework is likely installed correctly, it’s just that the terminal doesn’t know about it yet. So how do you tell the terminal about the new install? If you have this question, read on for some suggestions on how to answer it.

The first thing to know is that the terminal uses an environment variable called $PATH to determine where to look for installed commands. Since this is a variable, it is specific to your environment setup. There are two possible files where the terminal will look for your environment variables. Both are located in you home folder or ~/. To get to this folder in the terminal use cd ~/ or in Finder Cmd+Shift+G. The two files are named .zshrc or .bash_profile, the one in use will depend on which version of the shell you are using. To find this out use echo $SHELL in the Terminal. For zsh the output is /bin/zsh and for bash it is /bin/bash.

Now that you know what shell you are using, you know where to look for your environment variables. Open Terminal and change the directory to /~. Then use the cat command to display the contents of the file in Terminal. If you are using bash, make sure to substitute the bash file for the zsh file in the commands.

```
cd ~/
cat .zshrc
``` 
Now you know what is in your file and you should have an idea of what you want to add. To add to the file use the export command in the terminal along with the path to the files you installed. This example will use zsh and ruby 3.0.0 that was installed using homebrew. Keep in mind that the path and application will vary based on what is being installed and how you installed it.

```
echo 'export PATH="/usr/local/opt/ruby/bin:/usr/local/lib/ruby/gems/3.0.0/bin:$PATH"' >> ~/.zshrc
``` 
Once the command completes refresh your terminal session by using source ~/.zshrc or by closing the terminal and opening it again. Now when you run your command it should complete without the “Command Not Found” error. You may be asking, where do I find out where my is installed so I know what to add to my PATH. The answer to this depends on how the package was installed, and what version it is. In the logs from your package manager it will likely have the install location. If this is not available try searching for the default install location for your package manager and look there. If you still can’t find it, try installing the package again and see if the logs will tell you where it put the files.

