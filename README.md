# 引流

现在updateing实现了一个加载支持修改数据包内容的`EAPOL`认证客户端并将本工程的认证算法做成了插件，更加容易适配各个学校，建议大家尝试https://github.com/updateing/minieap，目前路由器不太支持`minieap`。

# 使用方法

## 安装

建议`Ubuntu`用户使用`Deb`包安装，`Fedora`用户使用`RPM`包安装，`Arch Linux`用户安装`AUR`中的`mentohust-git`

如果确定自己可以使用`xrgsu`认证成功，打开终端输入`sudo mentohust`运行即可
如果不确定，切换到锐捷所在目录，然后输入以下命令：

```bash
sudo mkdir /etc/mentohust
sudo cp ./8021x.exe  /etc/mentohust
sudo cp ./W32N55.dll /etc/mentohust
```

## 运行

然后打开终端输入`sudo mentohust`运行。如果认证失败，再切换到锐捷所在目录，输入以下命令：

```bash
sudo cp ./SuConfig.dat /etc/mentohust
```

然后打开终端输入`sudo mentohust`运行即可。
如果准确按以上步骤操作后还是认证失败，请下载`MentoHUSTTool`，在Windows下抓包并保存为`data.mpf`，
然后回到Linux，切换到`data.mpf`所在目录，输入以下命令：

```bash
sudo cp ./data.mpf /etc/mentohust
```

然后打开终端输入

```bash
sudo mentohust -f/etc/mentohust/data.mpf -w
```

运行即可。以后也只需输入`sudo mentohust`

也可以按下面的方法操作：

1. 静态IP用户请事先设置好IP；
2. 打开终端，输入`sudo mentohust`，回车；
3. ［正确］输入相应信息，如果认证成功，跳到第8步；如果提示“不允许使用的客户端类型”，按`Ctrl+C`结束认证；
4. 打开终端，输入`sudo mentohust -w -f'锐捷目录下任意文件路径'`，回车；
5. 如果认证成功，跳到第8步；如果提示“客户端完整性被破坏”，按`Ctrl+C`结束认证；
6. 将锐捷安装目录下的`SuConfig.dat`重命名为其他名字；
7. 打开终端，输入`sudo mentohust`，回车；
8. 如果是动态IP且不是Linux，打开相应设置去更新IP。
9. 以后认证只需打开终端，输入`sudo mentohust`，回车。
10. 要修改某些参数请输入`mentohust -h`查看帮助信息并据此修改，例如修改密码`sudo mentohust -pNewPassword -w`，要临时修改则不加`-w`参数。

## 如何退出

不以后台模式运行`mentohust`时，按Ctrl+C即可退出；后台运行时使用`sudo mentohust -k`退出认证。

## 查看帮助信息

```bash
mentohust -h
```

更详细的帮助信息请参考：[锐捷、赛尔认证MentoHUST](https://wiki.ubuntu.org.cn/%E9%94%90%E6%8D%B7%E3%80%81%E8%B5%9B%E5%B0%94%E8%AE%A4%E8%AF%81MentoHUST)

## 修改参数

请根据帮助信息操作，例如修改用户名和密码：

```bash
sudo mentohust -uUsername -pPassword -w
```

如果提示缺少`libpcap.so.0.x`而在`/usr/lib/`目录下已存在一个`libpcap.so.0.x.y`，输入以下命令：

```bash
sudo ln -s libpcap.so.0.x.y /usr/lib/libpcap.so.0.x
```


否则请安装`libpcap`

# 权责声明

1. 本程序所有涉及锐捷赛尔认证的功能均是来自前辈公开代码及抓包分析。
2. 本程序于个人仅供学习，于他人仅供方便认证，不得使用本程序有意妨害锐捷赛尔认证机制及相关方利益。
3. 一切使用后果由用户自己承担。
4. 本程序不提供任何服务及保障，编写及维护纯属个人爱好，随时可能被终止。
5. 使用本程序者，即表示同意该声明。谢谢合作。

# 链接

源码可在项目主页获取：http://mentohust.googlecode.com/

联系作者：在http://mentohust.googlecode.com/

留言或Email：mentohust@ehust.co.cc