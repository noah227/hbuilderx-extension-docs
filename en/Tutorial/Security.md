# HBuilderX被误报病毒木马的说明

首先说明，HBuilderX每次发版都会经过专业安全公司的单独检测。
通过后才会正式更新。请放心使用。
几年来，安全公司从未检测出一个病毒木马。但不给他们提交检测，他们就会乱报警告。

#### 360 审核截图

<img src="/static/snapshots/tutorial/Security_1.png" style="zoom: 80%;" />

#### 微软审核截图

<img src="/static/snapshots/tutorial/Security_2.png" style="zoom: 80%;" />

#### 为什么通过检测，有时我本机的微软杀毒软件仍然报警

`360`通过检测后一般实时更新，但`微软`的病毒定义库升级走的是`windows update`统一的机制，并且有一套自己的缓存机制。

在`Windows Defender`团队回复的内容中可知(见上图紫色方框)，需要用管理员身份运行命令行工具，执行命令才能清除缓存。

微软的回复是英文，我们翻译一下方便大家理解：

```
感谢您提交检测。
我们已审核了该文件，并已删除了检测结果。（之前的检测结果为有木马，在我们提交后微软回复删除了之前的结果，就是无毒的意思）
请尝试以下步骤清除缓存的检测并获取最新的恶意软件定义。
1.以管理员身份打开命令提示符，将目录更改为c:\Program Files\Windows Defender
2.运行“MpCmdRun.exe -removedefinitions -dynamicsignatures”
最新定义可从此处下载：https://www.microsoft.com/en-us/wdsi/definitions
最好的祝福，
Windows Defender 回复
```

另外红框中的"Not malware"，中文译为"并非恶意软件"。

#### 单独认证和推测算法的区别

除了`360`和微软，可能还有其他安全软件会误报病毒木马。这些都不用理睬，直接给HBuilderX加`白名单`。

原因如下：

各家安全软件，都是有一个推测算法，觉得有可能有病毒就会报，但经常误报。

不管是`360`还是`windows defender`都经常误报，比如：https://www.cnbeta.com/articles/tech/758679.htm

若软件开发者把软件单独提交给安全平台检测认证，此时走的不是推测算法，而是专业的、针对该软件的安全测试，在安全平台检测通过后会加白。

HBuilderX在未被360单独认证通过前，360一样报警。但认证通过后，360定义库自动更新，软件什么都不变，也不再被报警。

单独认证是一个严谨的、单独的、针对性的检测，不是推测算法，单独认证通过后就是真的没有病毒木马。目前国外的一些安全软件，包括微软、赛门铁克，并没有通畅的国内软件提交认证通道。但这些安全软件的推测算法并不准，所以对HBuilderX经常误报。

因为360提交方便、认证快，所以DCloud一般是等360单独认证通过后就会更新版本。在360单独认证HBuilderX无毒通过后，其他靠推测算法报警的安全软件的警告不用理睬。

各家安全软件都有扫描或信任白名单，把HBuilderX的目录设为信任目录即可。