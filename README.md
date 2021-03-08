# EdgeRouter_ER-X汉化
由于固件版本不同，需要使用不同的脚本进行优化
已上传为非压缩版 可以不用解压
若需要解压的可以使用 tar zxvf 进行解压

## EdgeRouter_ER-X——v1.x 固件版本为1.x的
直接下载后cd到文件夹中
命令语句
sudo ./er-en2zh make
切换为中文
sudo ./er-en2zh zh
切换为英语
sudo ./er-en2zh en

## EdgeRouter_ER-X——v2.x 固件版本为2.x的
直接下载后cd到文件夹中
命令语句
sudo ./er-en2zh make
切换为中文
sudo ./er-en2zh zh
切换为英语
sudo ./er-en2zh en


备注：2.X版本不存在ubnt-service-gui-start.sh这个文件了，所以导致上面部分用户说只有重启才能打开web。
修改方法如下，打开er-en2zh，把其中两处/usr/sbin/ubnt-service-gui-start.sh，修改为/usr/sbin/lighttpd -f /etc/lighttpd/lighttpd.conf保存，其余步骤参照原帖。
理论上是汉化通用的，不过其他机型未尝试，希望朋友尝试，并反馈。

