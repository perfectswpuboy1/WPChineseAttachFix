# WPChineseAttachFix
用于修复WordPress站点迁移后中文名附件无法显示问题的小工具

`2019-8-24 更新`:
1. 增加多级文件夹自动遍历功能
2. 修复部分中英混合文件名修改失效的问题
3. 代码重构至 pylint - 10.0/10.0 满分
4. 增加 typing 类型提示 (仅支持 Python 3.5+)

### 修复的问题类型：
很多WordPress站点站长在开始建站时候，会常常用中文给附件命名；
而之后迁移时候使用zip压缩程序将站点目录全部压缩，上传至新站点之后再解压。

这样经常会导致中文附件在WordPress程序中无法被索引（现象是出现大量的文章内图片404）；
原因是zip压缩会导致文件名的编码被改变。与数据库中所记录的图片文件名称不一样。
而这个时候在选择使用英文命名为时已晚。

### 修复的原理：
  将所有含有中文名称的附件全部以拼音命名；生成替换的sql指令，将WordPress数据库中的附件记录也改成拼音。

### 使用之前：
1. 请将wp-content/uploads的文件下载至本地并备份  
  *如果您的站点运行在自己的VPS上也可以直接对该文件夹进行操作，但请注意备份*  
  并确保程序有操作文件夹的权限
2. 将您要操作的数据库备份
3. 请安装pypinyin第三方库  
    *安装方式：命令行输入 `pip install pypinyin` 即可*

### 使用方法：
- 在终端/命令行使用时，输入：python main.pyw [路径]  
   *请确定您的默认Python版本为Python3.5+，否则请更新Python并输入：Python3 main.pyw [路径]*
  
- 在图形化界面使用时，请直接打开，选择文件夹，然后点击开始运行即可

在执行完毕之后，程序会打开生成的sql.txt文件，请将里面的所有语句全部拷贝至SQL终端执行
之后将文件夹中的全部重命名之后的文件回传至uploads文件夹

### 注意：如果附件没有在文章中发布过，其数据库的更改很可能无效
### 注意：请务必在使用前备份要操作的文件和数据库，因为使用该工具而导致的数据出错/丢失作者不负责任

> 该软件是作者在使用 https://www.wpdaxue.com/wordpress-images-chinese-name-garbled.html 这里的工具总是失败之后无奈重写的一个版本。不过在此非常感谢原Framework版本作者 wp大学的@木子 提供的思路。

祝使用愉快O(∩_∩)O~~
