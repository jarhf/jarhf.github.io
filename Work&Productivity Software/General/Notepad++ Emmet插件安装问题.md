#Notepad++ Emmet插件在win10下安装后无效的问题
使用Expand Abbreviation会弹出python script错误，解决办法：
1. 先卸载安装Emmet时自动安装的Python Script插件。
2. 从https://sourceforge.net/projects/npppythonscript下载安装python script。
我安装有个奇怪的问题，默认安装路径C:\Program Files (x86)\notepad++,怎么都改不成Program Files,但是改成其他目录就行。
于是只好先安装在x86目录下（可能他检测到我的notepad是32位的），由于我的notepad++是安装在Program Files目录下，会找不到python script插件，把x86下的python script剪切过去就好了。
3. Emmet默认快捷键不是Tab，建议修改成Tab
 Settings=>Shortcut mapper=>Plugin commands=>Expand abbreviation
