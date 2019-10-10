---
title: Git钩子的一次尝试使用
date: 2019-10-07 21:31:59
tags:
    - GitHub
categories:
    - 学习
    - GitHub
---

### 思路
1. 在执行commit命令后，提取log
2. 寻找关键词
3. 触发推送

### 具体流程
1. 配置远程仓库  origin  
2. 使用ssh免输入方式进行推送
3. 编写hook脚本post-commit  
```bash
############################
# 特定词触发push gh-pages
# Author: 
############################

# 触发词
tword="触发词" # 

echo "触发post-commit钩子"

# 截取触发词
lmsg=$(git log -1 --pretty=format:"%h - %an, %ar : %s")
kword=${lmsg:0-5}
# 判断是否push
if test $kword = $tword
then
    echo "满足条件，开始推送到gh-pages"
    $(git push origin master:hexo-g)
    echo "完成push工作"
    exit 0
else
    echo "只是commit，没有触发推送"
fi
```

### 参考
[Git - 查看提交历史](https://www.git-scm.com/book/zh/v2/Git-基础-查看提交历史)  
[Shell 字符串](https://www.runoob.com/linux/linux-shell-variable.html)  
[github本地git push ssh方式免用户名和密码配置相关问题](https://blog.csdn.net/lonyw/article/details/75392410)   
