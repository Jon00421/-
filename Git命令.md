# Git命令

<a name="8T83Y"></a>
# Git命令


- 查看是否生成SSH~~:
```git
  cat ~/.ssh/id_rsa.pub
```

- 生成SSH:
```git
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- 告诉git你的名字邮箱
```git
  git config --global user.name "your_name"
   git config --global user.email "your_email@example.com"
```

- 克隆仓库
```git
  git clone 仓库地址（SSH地址）
```

- git提交三部曲
```git
 1. git add (git add -A)
 2. git commit (git commit -m "本次提交的修改的备注")
 3. git push
    1. 第1次提交到本分支  （git push origin main）
    2. 第2-n次提交到本分支 （git push）
    3. 提交到其他分支  （git push origin b）
```

- 代码冲突
```git
  git pull（抓取远程仓库的内容，协同开发时，每一次提交之前，git pull）
```
