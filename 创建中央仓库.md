

# 创建中央仓库

以下是在服务器上创建中央仓库的过程：

1. 在服务器上新建一个目录作为中央仓库，例如 `/home/myproject.git`：

```bash
mkdir /home/myproject.git
```

2. 进入到该目录并初始化 Git 仓库：

```bash
cd /home/myproject.git
git init 
```

3. 在本地 PC 上生成公钥，可以使用您在 PC 上的邮箱地址：

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

4. 将生成的公钥添加到服务器的 authorized_keys 文件中，以便您能够通过 SSH 协议连接到服务器：

```bash
cat ~/.ssh/id_rsa.pub | ssh root@114.132.175.215 "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

5. 在本地 PC 的项目目录中添加中央仓库的地址：

```bash
cd /path/to/project
git remote add origin ssh://root@114.132.175.215:/home/myproject.git
```

6. 拉取远程仓库的内容到本地，并将其合并到本地的 `master` 分支（如果需要）：

```bash
git pull origin master
```

7. 完成修改后，将本地的 `master` 分支推送到中央仓库的 `master` 分支：

```bash
git push origin master
```

这样就完成了在服务器上创建中央仓库的过程，并将本地项目推送到中央仓库中。
