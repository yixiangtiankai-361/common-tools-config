# 一、安装

# 二、配置

## 1、用户名和邮箱

```shell
# 查看全局配置
git config --global --list
# 全局配置
git config --global user.name "test"
git config --global user.email test@qq.com
# 清除
git config --global --unset user.name "test"
git config --global --unset user.email test@qq.com
# 本地配置
git config  user.name 'test'
git config  user.email test@qq.com
```

## 2、生成 SSH keys

```shell
# github
ssh-keygen -t rsa -C 'github邮箱号' -f ~/.ssh/id_rsa_github
# gitee
ssh-keygen -t rsa -C 'gitee邮箱号' -f ~/.ssh/id_rsa_gitee
```

## 3、配置 github 和 gitee

### 3.1 github

* Settings -> Access -> SSH and GPG keys -> New SSH key

![](./assets/GitHub%E7%9A%84SSH%E5%85%AC%E9%92%A5%E8%AE%BE%E7%BD%AE.png)

![](./assets/GitHub%E6%96%B0%E5%A2%9ESSH%E5%85%AC%E9%92%A5.png)

### 3.2 gitee

* 设置 -> 安全设置 -> SSH 公钥 -> 粘贴 id_rsa_gitee.pub 内容

![](./assets/Gitee%E7%9A%84SSH%E5%85%AC%E9%92%A5.png)

## 4、配置 config

```shell
# 在 .ssh 目录下新建 config 文件
touch config
# 使用 vim 命令往 config 文件中写入相关配置
vim config -> i # 按 i 进入编辑模式
# gitee
Host gitee.com
HostName gitee.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_gitee
# github
Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_github
```

## 5、测试

```shell
# 测试 github
ssh -T git@github.com
# 测试 gitee
ssh -T git@gitee.com
```

## 6、使用

```shell
# 拉取 github 远程仓库
git clone git@github.com:仓库地址
# 本地已有仓库推送 github 远程仓库
git remote add origin git@github.com:仓库地址
# github 新仓库同步到本地
echo "# 仓库名" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:仓库地址
git push -u origin main
```
