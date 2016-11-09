# -TortoiseGit-Bad-file-number

报错信息：
/usr/libexec/git-core/git-sh-setup: line 86: /usr/bin/sed: Bad file number
remote: Counting objects: 6, done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 6 (delta 3), reused 0 (delta 0)
From git.dev.sh.ctripcorp.com:tieyou_bus/ctrip_bus_common_api
= [up to date]      tars_release -> origin/tars_release
= [up to date]      master     -> origin/master
5f84256..0b4e3bb  tars_uat   -> origin/tars_uat
* [new tag]         ctrip_bus_common_api201611031722 -> ctrip_bus_common_api201611031722
C:\Program Files (x86)\Git/libexec/git-core\git-pull: line 265: /usr/bin/tr: Bad file number
Your configuration specifies to merge with the ref 'tars_release'
from the remote, but no such ref was fetched.


原始.git/config配置文件如下：
[core]  
    repositoryformatversion = 0  
    filemode = false  
    bare = false  
    logallrefupdates = true  
    symlinks = false  
    ignorecase = true  
    hideDotFiles = dotGitOnly  
[remote "origin"]  
    url = https://github.com/cncounter/translation.git  
    fetch = +refs/heads/*:refs/remotes/origin/*  
[branch "master"]  
    remote = origin  
    merge = refs/heads/master  
[remote]  
    pushdefault = origin  
[credential]  
    helper = store 
    
    
修改为：
[core]  
    repositoryformatversion = 0  
    filemode = false  
    bare = false  
    logallrefupdates = true  
    symlinks = false  
    ignorecase = true  
    hideDotFiles = dotGitOnly  
[remote "origin"]  
    url = https://github.com/cncounter/translation.git  
    fetch = +refs/heads/*:refs/remotes/origin/*  
[branch "master"]  
    remote = origin master  
    merge = refs/heads/master  
[remote]  
    pushdefault = origin  
[credential]  
    helper = store  
    
    
branch master 下 remote = origin 修改为 remote = origin master;（使用tars_release）
