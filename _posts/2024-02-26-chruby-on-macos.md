---
title: "Updating the blog on MacOS"
date: 2024-02-26 22:35:00 +0900 
categories: [notes]
tags: [github, git, churby, ruby, jekyll, en] #lang tag: en, jp, zh
---


# 1. Setup
## 1.1. Install `Chruby`
To solve the ["You don't have write permissions for the /Library/Ruby/Gems/2.3.0 directory. (Mac user)"](https://stackoverflow.com/questions/51126403/you-dont-have-write-permissions-for-the-library-ruby-gems-2-3-0-directory-ma) issue, open the terminal on MacOS and enter the following commands:
```powershell
brew install chruby ruby-install
``` 

Then install the latest `Ruby`:
```powershell
ruby-install ruby
```  
## 1.2. Configure Chruby

Check Chruby-related commands:
```powershell
brew info chruby
```  

The output may look like following:

![chrupy setup](https://raw.githubusercontent.com/melposyrup/imageHost/main/img/202402262310.png)

To add the basic and auto configuration to `zsh` file, you need to open the `zsh` file with VSCode:
```powershell
code ~/.zshrc
```

Write those two lines of configuration, and switch ruby mannually (optional):
```powershell
source [your path]/chruby.sh
source [your path]/chruby/auto.sh
chruby ruby-3.3.0[or your ruby-version]
```

Save the file and load the configuration by entering:
```powershell
source ~/.zshrc
``` 
Then restart the terminal.

After that, install dependencies:
```powershell
gem install jekyll
gem install bundler
``` 
 
 
### 1.2.1. If `code .` Command Is Not Recognized

Follow these steps to install the code command in PATH:

1. Open VSCode.
2. Press `Shift+Cmd+P` to open the command palette.
3. Type `Shell Command: Install 'code' command in PATH`.
4. Select and execute the command from the search results.
5. Restart the terminal.
After this operation, VSCode will add the code command to your environment variables, allowing you to use the `code .` command in the terminal to open the project in current directory.

### 1.2.2. If You Encounter `EACCES: permission denied, unlink '/usr/local/bin/code'`

Use the following command to delete `/usr/local/bin/code`:
```powershell
sudo rm /usr/local/bin/code
``` 
Then repeat the process to install the `code` command in PATH.

## 1.3. Open Your Blog Repository with VSCode

The following command will clone the repository to the default directory:
```powershell
git clone [your url]
```  

List all files and folders in the default directory:
```powershell
ls
``` 

Find the blog folder and change the directory to it:
```powershell
cd [your directory name]
``` 

Open the project with VSCode:
```powershell
code .
``` 

Check the versions:
```powershell
ruby -v
chruby --version
gem -v
jekyll -v
bundler -v
```

Delete the Gemfile.lock file, and regenerate the configuration with the following commands:
```powershell
bundle 
bundle install
bundle exec jekyll s
```
Check for changes in http://127.0.0.1:4000

### 1.3.1. If There Are Compatibility Issues Between Jekyll and Ruby

If you encounter an error report similar to the following:
```powershell
jekyll 4.3.2 | Error:  undefined method `[]' for nil
/Users/molchin/.rubies/ruby-3.3.0/lib/ruby/3.3.0/logger.rb:384:in `level': undefined method `[]' for nil (NoMethodError)
``` 
Use the following commands to update `gem`:
```powershell
gem update
gem install bundler
bundle update
```


# 2. Update Your Blog

Edit or add `.md` files, preview the effect at http://127.0.0.1:4000, then stop the preview by pressing `ctrl + c`.
Enter the following command to update the `gemfile.lock` file:
```powershell
bundle lock --add-platform x86_64-linux
```

Then proceed with the usual upload:
```powershell
git add --all
git commit -m "Update _config && Generate Gemfile.lock"
git push
```

# 3. Congratulations
Now you are able to update your blog on MacOS, which can be more stable compared to Windows. 
Have fun!

## 3.1. References
- [You don't have write permissions for the /Library/Ruby/Gems/2.3.0 directory. (mac user)](https://stackoverflow.com/questions/51126403/you-dont-have-write-permissions-for-the-library-ruby-gems-2-3-0-directory-ma)
