# CLI commands notes

Table of contents

* [1. Archives](#markdown-header-1-archives)

* [2. Mysql dump](#markdown-header-2-mysql-dump)

* [3. Work with files](#markdown-header-2-mysql-dump)

* [4. Git](#markdown-header-4-git)

* [5. SVN](#markdown-header-5-svn)

* [6. Other](#markdown-header-6-other)

* [7. Work with processes](#markdown-header-7-work-with-processes)

* [8. Mac OS](#markdown-header-8-mac-os)

- - -

### 1. Archives
Pack
```
tar --exclude="bitrix/backup/*" --exclude="bitrix/cache/*" --exclude="bitrix/managed_cache/*" --exclude="bitrix/stack_cache/*" --exclude="bitrix/html_pages/*" -zcvf bitrix.tar.gz ./bitrix
tar -zcvf git.tar.gz ".git"
```
Unpack
```
tar -zxvf bitrix.tar.gz
```

### 2. Mysql dump
Export
```
mysqldump --opt -u USER -p DBNAME > dbname.sql
```
Import
```
mysql -u USER -p DBNAME < dbname.sql
```

### 3. Work with files
Remove directories
```
rm -rf mydir
```
Show dir sizes
```
du -sh *
```
Show size of specific dir
```
du -sh mydir
```
Remove 0 size files
```
find /tmp -size  0 -print0 |xargs -0 rm
```
See last 10 lines
```
tail -F file.log
```
See first 10 line
```
head file.log
```
Symlinks
```
ln -s /path/to/file /path/to/symlink
```
Change owner
```
chown -Rc w19_admin:psacln .;chown -c w19_admin:psaserv .
```
Change permitions
```
chmod -R 755 /var/www

find * -type d -print0 | xargs -0 chmod 0755 # for directories
find . -type f -print0 | xargs -0 chmod 0644 # for files
```

### 4. Git
Add repo to existing folder
```
git init
git remote add origin PATH/TO/REPO
git fetch
git reset --hard origin/master
```
Track remote branch
```
git branch --set-upstream master origin/master
```
New remote URL
```
git remote set-url origin new-url
```
Clone from SVN repo
```
git svn clone -s http://source.epages.su/svn/nasosik/
```

### 5. SVN
New svn repo
```
svnadmin create /var/svn/repos
```

### 6. Other
Find files with BOM
```
grep -rl $'\xEF\xBB\xBF' .
```
Plesk php
```
/opt/plesk/php/5.6/bin/php
```

### 7. Work with processes
```
ps aux | less
netstat -nlpt | grep 8080
ps ax | grep jira | grep -v grep
```

### 8. Mac OS
Add spaces to dock
```
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}'
```
Stop mysql, apache
```
sudo launchctl unload -F /Library/LaunchDaemons/com.oracle.oss.mysql.mysqld.plist
sudo apachectl -k stop
```
Disable mail
```
/etc/postfix/main.cf
default_transport = error:This server sends mail only locally.
```
Secondary skype
```
alias skype2='sudo /Applications/Skype.app/Contents/MacOS/Skype /secondary'
```
