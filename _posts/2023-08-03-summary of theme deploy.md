---
title: "Deploying jekyll-theme-chirpy on Windows"
date: 2023-08-03 17:45:00 +0900 
categories: [notes]
tags: [github, git, ruby, jekyll, en] #lang tag: en, jp, zh
---

***I would like to extend my sincere gratitude to [Techno Tim](https://www.youtube.com/watch?v=F8iOU1ci19Q) and [Jadehawk](https://www.youtube.com/watch?v=5z7_qp0CWBY) for their instructional videos on deploying jekyll-theme-chirpy on Windows. Their guidance has been of great help to me.***

# Before th start
## 1. Installing [Git](https://git-scm.com/)   
![Check on `Open Git Bash here` is recommended](https://raw.githubusercontent.com/melposyrup/imageHost_forPersonalUse/main/img/20230803165143.png)  
Check the `Open Git Bash here`.

## 2. Installing [Ruby](https://rubyinstaller.org/downloads/)  
Choose Ruby+Devkit,   
![Install all of them](https://raw.githubusercontent.com/melposyrup/imageHost_forPersonalUse/main/img/20230803181042.png)    
And install all of them.  

## 3. Installing Jekyll  
After Ruby is installed, open terminal and run: 
```powershell
gem install jekyll
```  
## 4. Installing Bundler  
In terminal:
```powershell
gem install bundler
```   
Have a check on dependencies:
```powershell
ruby -v
gem -v
jekyll -v
bundler -v
```   

# Start with [Chirpy Starter](https://github.com/cotes2020/chirpy-starter)  

## 1. Create repository
Click the link `use this template`,   
name the new repository as `GITHUB-USERNAME.github.io`, `Public`,   
click the button `Create`.

## 2. Clone repo to PC
In powershell/terminal, use `CD` to change directory. For instance:
```powershell
PS C:\Users\Admin> CD D:\Github
PS D:\Github>
```  
Find URL in `Clone`, `HTTPS` on your repo code page.  
Paste it into terminal as following:
```powershell
git clone URL
```  
Open project folder with you editor (VScode is highly recommended).  
  
**Open `.gitignore` with txt, find `Gemfile.lock` and delete.**
  
## 3. Update `_config.yml`
Make some changes on variables:
- timezone: e.g. Tokyo
- title: e.g. My Blog
- tagline e.g. For notes and documents
- url: e.g. https://username.github.io
- avatar: URL of picture

Open terminal (make sure your directory are inside the project folder),  
run the following command line by line:
```powershell
bundle 
bundle install
bundle exec jekyll s
```  

`GemFile.lock` file should be now generated.   
Check for changes in http://127.0.0.1:4000

## 4. Update `Gemfile.lock`
Before upload, run the following command:
```powershell
bundle lock --add-platform x86_64-linux
```  

## 5. Upload to github
```powershell
git add --all
git commit -m "Update _config && Generate Gemfile.lock"
git push
```  
**As of the version released before 2023-08-03, `gh-pages` branch will be not automatically generated.**  
But it works well anyway.

# Good job
Open your `username.github.io`, and everything should be good.   
To update the blog, you can add .md files to the `_posts` folder via an editor,   
or you can write them directly on the GitHub web page.   
Both methods work. Have a fun!


### Documents
- [Chirpy - Getting Started](https://chirpy.cotes.page/posts/getting-started/)

- [Jekyll on Windows](https://jekyllrb.com/docs/installation/windows/)
