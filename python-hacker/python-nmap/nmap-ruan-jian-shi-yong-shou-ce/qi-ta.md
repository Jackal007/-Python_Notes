# 其他

本节描述一些重要的\(和并不重要\)的选项，这些选项 不适合其它任何地方。

-6 \(启用IPv6扫描\)

从2002年起，Nmap提供对IPv6的一些主要特征的支持。ping扫描\(TCP-only\)、 连接扫描以及版本检测都支持IPv6。除增加-6选项外， 其它命令语法相同。当然，必须使用IPv6地址来替换主机名，如 3ffe:7501:4819:2000:210:f3ff:fe03:14d0。 除“所关注的端口”行的地址部分为IPv6地址。

IPv6目前未在全球广泛采用，目前在一些国家\(亚洲\)应用较多， 一些高级操作系统支持IPv6。使用Nmap的IPv6功能，扫描的源和目 的都需要配置IPv6。如果ISP\(大部分\)不分配IPv6地址，Nmap可以采用 免费的隧道代理。一种较好的选择是BT Exact，位于[https://tb.ipv6.btexact.com/](https://tb.ipv6.btexact.com/)。 此外，还有Hurricane Electric，位于[http://ipv6tb.he.net/](http://ipv6tb.he.net/)。6to4隧道是 另一种常用的免费方法。

-A \(激烈扫描模式选项\)

这个选项启用额外的高级和高强度选项，目前还未确定代表 的内容。目前，这个选项启用了操作系统检测\(-O\) 和版本扫描\(-sV\)，以后会增加更多的功能。 目的是启用一个全面的扫描选项集合，不需要用户记忆大量的 选项。这个选项仅仅启用功能，不包含用于可能所需要的 时间选项\(如-T4\)或细节选项\(-v\)。

--datadir

&lt;

directoryname

&gt;

\(说明用户Nmap数据文件位置\)

Nmap在运行时从文件中获得特殊的数据，这些文件有 nmap-service-probes， nmap-services， nmap-protocols， nmap-rpc， nmap-mac-prefixes和 nmap-os-fingerprints。Nmap首先 在--datadir选项说明的目录中查找这些文件。 未找到的文件，将在BMAPDIR环境变量说明的目录中查找。 接下来是用于真正和有效UID的~/.nmap 或Nmap可执行代码的位置\(仅Win32\)；然后是是编译位置， 如/usr/local/share/nmap 或/usr/share/nmap。 Nmap查找的最后一个位置是当前目录。

--send-eth \(使用原以太网帧发送\)

要求Nmap在以太网\(数据链路\)层而不是IP\(网络层\)发送 报文。默认方式下，Nmap选择最适合其运行平台的方式，原套接 字\(IP层\)是UNIX主机最有效的方式，而以太网帧最适合Windows操作 系统，因为Microsoft禁用了原套接字支持。在UNIX中，如果没有其 它选择\(如无以太网连接\)，不管是否有该选项，Nmap都使用原IP包。

--send-ip \(在原IP层发送\)

要求Nmap通过原IP套接字发送报文，而不是低层的以 太网帧。这是--send-eth选项的补充。

--privileged \(假定用户具有全部权限\)

告诉Nmap假定其具有足够的权限进行源套接字包发送、 报文捕获和类似UNIX系统中根用户操作的权限。默认状态下， 如果由getuid\(\)请求的类似操作不为0，Nmap将退出。 --privileged在具有Linux内核性能的类似 系统中使用非常有效，这些系统配置允许非特权用户可以进行 原报文扫描。需要明确的是，在其它选项之前使用这些需要权 限的选项\(SYN扫描、操作系统检测等\)。Nmap-PRIVILEGED变量 设置等价于--privileged选项。

--interactive \(在交互模式中启动\)

在交互模式中启动Nmap，提供交互式的Nmap提示，便于 进行多个扫描\(同步或后台方式\)。对于从多用户系统中扫描 的用户非常有效，这些用户常需要测试他们的安全性，但不希望 系统中的其它用户知道他们扫描哪些系统。使用--interactive 激活这种方式，然后输入**h**可 获得帮助信息。由于需要对正确的shell程序和整个功能非常熟悉， 这个选项很少使用。这个选项包含了一个!操作符，用于执行shell命令， 这是不安装Nmap setuid root的多个原因之一。

-V; --version \(打印版本信息\)

打印Nmap版本号并退出。

-h; --help \(打印帮助摘要面\)

打印一个短的帮助屏幕，列出大部分常用的 命令选项，这个功能与不带参数运行Nmap是相同的。

