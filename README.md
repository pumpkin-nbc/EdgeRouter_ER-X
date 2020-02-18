# EdgeRouter_ER-X
关于ER-X汉化测试
从UBNT论坛找到，转载到这，希望有需要的朋友继续帮忙维护，本人也会尝试维护该代码

原贴内容：
看到不少EdgeRouter的汉化模板，觉得太局限了，都是拿某个版本的模板改，然而固件一更新就出问题。
换个思路，抓取这些模板的标签，搞个字典直接替换就不受版本限制了，最多新版本出现的新词汇没得翻译，需要在字典里添加，也就是只剩下字典维护的工作，一般人都能做吧。
so，顺手写个替换脚本，外加一个初始字典，尝试另一个新路子。自已测试过，效果还不错。
使用方法：
下载翻译工具，一个脚本程序，再下载字典，都解压到同个目录下。进入到这个目录，执行：

sudo ./er-en2zh make
程序会把原来的备份，再从备份按字典一个个翻译存到新目录。字典改动或者固件升级，再执行一次就可以了。
翻译完后，输入：

sudo ./er-en2zh zh
几秒后去刷新浏览器就是中文界面了。重回原版的话输入：

sudo ./er-en2zh en
一样是几秒后刷新就可以，根本不需要重启路由器！！！

这种方法最大的特点:
1, 没有型号、版本依赖。升级固件后再运行一次就可以了，大不了新词汇找不到还是E文而已。
2, 安全。也就是一个简单的脚本，谁都能打开来看，不象其它编译的程序或是别人弄好的模板，要担心有没夹带私货。
3, 还是安全。原理只是替换E文标签，不改变原有的结构功能，升级固件什么的都不影响。
4, 切换语言无须重启。只需要一个命令，二三秒时间再刷新下浏览器就可以了。
5, 字典开放，任何人都可以参与维护，说不定UBNT到时候做i18n时会用到这个字典。

正常的命令和输出应该这样：
'''
~$ sudo ./er-en2zh make
Old Chinese templates exist, deleting... ok
Copy original templates... ok
Reading dictionary... ok
Translating... ok
Run "sudo ./er-en2zh zh" will change WebUI to Chinese, "sudo ./er-en2zh en" will restore to original version.
~$ sudo ./er-en2zh zh
WebUI change to Chinese. HTTP daemon restarting... ok
'''

备注：2.X版本不存在ubnt-service-gui-start.sh这个文件了，所以导致上面部分用户说只有重启才能打开web。
修改方法如下，打开er-en2zh，把其中两处/usr/sbin/ubnt-service-gui-start.sh，修改为/usr/sbin/lighttpd -f /etc/lighttpd/lighttpd.conf保存，其余步骤参照原帖。
理论上是汉化通用的，不过其他机型未尝试，希望朋友尝试，并反馈。

本人整合了一下代码 PS：还未尝试，等ER-X到
上传路由器
cd 文件
tar zxvf er-dict-190501.tar.gz
tar zxvf er-en2zh-0.99.ER.noarch.tar.gz

~$ sudo ./er-en2zh make
Old Chinese templates exist, deleting... ok
Copy original templates... ok
Reading dictionary... ok
Translating... ok
Run "sudo ./er-en2zh zh" will change WebUI to Chinese, "sudo ./er-en2zh en" will restore to original version.

~$ sudo ./er-en2zh zh
WebUI change to Chinese. HTTP daemon restarting... ok
'''
