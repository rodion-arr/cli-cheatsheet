# CLI commands notes

Table of contents

* [1. Archives](#1-archives)

* [2. Mysql dump](#2-mysql-dump)

* [3. Work with files](#3-work-with-files)

* [4. Git](#4-git)

* [5. SVN](#5-svn)

* [6. Other](#6-other)

* [7. Work with processes](#7-work-with-processes)

* [8. Mac OS](#8-mac-os)

* [9. DigitalOcean](#9-digitalocean)

- - -

### 1. Archives
Pack
```
#!bash
tar --exclude="bitrix/backup/*" --exclude="bitrix/cache/*" --exclude="bitrix/managed_cache/*" --exclude="bitrix/stack_cache/*" --exclude="bitrix/html_pages/*" -zcvf bitrix.tar.gz ./bitrix
tar -zcvf git.tar.gz ".git"
```
Unpack
```
#!bash
tar -zxvf bitrix.tar.gz
```
Unpack and skip existing files
```
#!bach
tar --skip-old-files -zxvf bitrix.tar.gz
```
Pack and split by size
```
#!bash
tar cvzf - dir/ | split --bytes=200MB - sda1.backup.tar.gz.
```
Unpack multiple parts
```
#!bash
cat sda1.backup.tar.gz.* | tar xzvf -
```

### 2. Mysql dump
Export
```
#!bash
mysqldump --opt -u USER -p DBNAME > dbname.sql
```
Import .sql file
```
#!bash
mysql -u USER -p DBNAME < dbname.sql
```
Import .sql.qz file
```
#!bash
gunzip -cd dump.sql.gz | mysql -u USER -p DBNAME
```

### 3. Work with files
Remove directories
```
#!bash
rm -rf mydir
```
Show dir sizes
```
#!bash
du -sh *
```
Show size of specific dir
```
#!bash
du -sh mydir
```
Remove 0 size files
```
#!bash
find /tmp -size  0 -print0 |xargs -0 rm
```
See last 10 lines
```
#!bash
tail -F file.log
```
See first 10 line
```
#!bash
head file.log
```
Symlinks
```
#!bash
ln -s /path/to/file /path/to/symlink
```
Change owner
```
#!bash
chown -Rc w19_admin:psacln .;chown -c w19_admin:psaserv .
```
Change permitions
```
#!bash
chmod -R 755 /var/www

find * -type d -print0 | xargs -0 chmod 0755 # for directories
find . -type f -print0 | xargs -0 chmod 0644 # for files
```
Find text in file
```
#!bash
grep --include=\*.{xml,php} -rnw '/path/to/somewhere/' -e "pattern"
```
Find directory by name
```
#!bash
find  / -name "apt"
```

### 4. Git
Add repo to existing folder
```
#!bash
git init
git remote add origin PATH/TO/REPO
git fetch
git reset --hard origin/master
```
Track remote branch
```
#!bash
git branch --set-upstream master origin/master
```
New remote URL
```
#!bash
git remote set-url origin new-url
```
Clone from SVN repo
```
#!bash
git svn clone -s http://source.epages.su/svn/nasosik/
```
Update Git CentOS
```
#!bash
yum install http://opensource.wandisco.com/centos/6/git/x86_64/wandisco-git-release-6-1.noarch.rpm
yum install git
git --version
```
Get repo from site by HTTP
```
#!bash
git clone http://chaosdorf.de/.git/
curl http://chaosdorf.de/.git/HEAD
curl http://chaosdorf.de/.git/refs/heads/master
git http-fetch -a 57104ea967fc24763ead9c57d3463a80e9d05eea http://chaosdorf.de/.git
git checkout 57104ea967fc24763ead9c57d3463a80e9d05eea
```

### 5. SVN
New svn repo
```
#!bash
svnadmin create /var/svn/repos
```

### 6. Other
Find files with BOM
```
#!bash
grep -rl $'\xEF\xBB\xBF' .
```
Plesk php
```
#!bash
/opt/plesk/php/5.6/bin/php
```

### 7. Work with processes
```
#!bash
ps aux | less
netstat -nlpt | grep 8080
ps ax | grep jira | grep -v grep
```

### 8. Mac OS
Add spaces to dock
```
#!bash
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}'
```
Stop mysql, apache
```
#!bash
sudo launchctl unload -F /Library/LaunchDaemons/com.oracle.oss.mysql.mysqld.plist
sudo apachectl -k stop
```
Disable mail
```
#!bash
/etc/postfix/main.cf
default_transport = error:This server sends mail only locally.
```
Secondary skype
```
#!bash
alias skype2='sudo /Applications/Skype.app/Contents/MacOS/Skype /secondary'
```

### 9. DigitalOcean
Ubuntu 16 nginx `/etc/nginx/`
```
#!bash
sudo systemctl restart nginx
sudo systemctl stop nginx
sudo systemctl start nginx
nginx -t
```
