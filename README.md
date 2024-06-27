<h1 align="center">
	<img src="image/xapp_logo.png" alt="xpoc" width="200px">
	<br>
</h1>

<h3 align="center">专注于web指纹识别的工具</h3>

<p align="center">
  <img src="https://img.shields.io/github/release/chaitin/xapp.svg" />
  <a href="https://docs.xray.cool/tools/xapp/BasicIntroduction">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" target="_blank" />
  </a>
</p>

<p align="center">
  <a href="#-快速开始">快速开始</a> •
  <a href="#-特点">特点</a> •
  <a href="#-安装使用">使用</a> •
  <a href="#-贡献-poc">贡献</a> •
  <a href="https://github.com/chaitin/xpoc/releases">下载</a> •
  <a href="https://docs.xray.cool/tools/xapp/QuickStart">使用文档</a> 
</p>

---

## 🚀 快速使用

**在使用之前，请务必阅读并同意 [License](./LICENSE.md) 文件中的条款，否则请勿安装使用本工具。**

1. 指定指纹扫描单个目标：

```bash
xapp -r xxx.yml -t https://www.example.com
echo https://www.example.com | xapp -r xxx.yml
```

2. 指定指纹扫描多个目标：

```bash
xapp -r xxx.yml -t https://www.example.com -t https://www.example2.com
xapp -r xxx.yml -i targets.txt
cat targets.txt | xapp -r xxx.yml
```

3. 指定多个指纹进行扫描：

```bash
xapp -r xxx.yml -r yyy.yml -t https://www.example.com
xapp -r "./finger/web/*.yml" -t https://www.example.com
xapp -r "./finger/**/*.yml" -t https://www.example.com
```

4. 指定group进行扫描：

```bash
xapp -g web.list -t https://www.example.com
```

## 🪟 特点

1. 支持web指纹识别，可以快速识别web目标的技术栈，为安全测试提供基础数据。
2. 规则语法与xray PoC保持一致，简单易懂，适合新手开发者快速上手。
3. 自定义指纹规则，实现精细逻辑分支，增强识别的准确性和灵活性。
4. 开放共创：鼓励社区参与，共同在GitHub上构建标准的[指纹规则集](https://github.com/chaitin/xray-plugins)，分享自己的指纹规则集，免费供所有人使用。
5. 性能优化：专门针对同时加载大量指纹的场景进行优化，提高运行效率。

## 📦 安装使用

在[releases](https://github.com/chaitin/xapp/releases)中下载对应的系统的最新版即可，运行`xpoc -h`即可查看帮助

```bash
  __  /\    ___.   /\_.   /\_.
  | |/ /   /   |  / __.\ / __.\
  |   /XRAY™/| | / /_/ // /_/ /
 /   |   / ___ |/ .___// .___/
/ /|_|  / /  |_/_/    /_/
\/0.0.0\/
[INF] 24-06-26 22:25:33 使用以下位置的配置文件：/root/.xray/xapp/xapp-config.yaml [app.go:422]
XAPP:


示例:
     Scan single target:       xapp -t http://192.168.1.1:8000
     └>  multiple targets:     xapp -t http://192.168.1.1:8000 -t http://192.168.1.1:8001
     └>  target file:          xapp -i a.txt
     Show plugin:              xapp -v
     └>  run one plugin:       xapp -t tcp://192.168.1.1:8000 -r "./finger/finger.yml"
     └>  run plugins:          xapp -t tcp://192.168.1.1:8000 -r "./finger/*.yml"


描述:
   web application scanner

命令:
   lint     对 yaml 脚本进行静态格式校验
   score    对 yaml 指纹脚本进行评分
   help, h  Shows a list of commands or help for one command

选项:
   HTTP客户端：
     --hrps value, --host_rps value             对于单个Host的每秒最大发送请求数: 小于等于0时不限制每秒最大发送请求数 (default: 0)
     --http-proxy value [ --http-proxy value ]  HTTP客户端代理: [http|https|socks5://][username[:password]@]host[:port] 仅对http连接生效
     --retry value                              请求失败重试次数 (default: 2)

   插件展示：
     -v  列出启用的插件 (default: false)

   日志管理：
     --debug            调试：打印debug日志 (default: false)
     --log-level value  指定等级：debug/info(默认)/warn/error/fatal/disable
     --silent           静默：不打印banner，日志等级设置为fatal (default: false)

   目标拆解：
     -i value               目标文件: 指定含有扫描目标的文本文件
     -t value [ -t value ]  扫描目标: 可以为URL/IP/域名/Host:Port等多种形式的混合输入 （默认）

   结果输出：
     -o value [ -o value ]  结果输出: 指定保存结果的文件路径

   设置变量：
     --env value [ --env value ]  设置系统变量

   连接管理：
     --proxy value    全局代理：socks5://[username[:password]@]host[:port] 仅支持socks5，对所有连接生效
     --timeout value  读超时: 从连接中读取数据的最大耗时 (default: 5s)

   通用：
     --config value                                           配置文件：使用指定的配置文件，如果文件不存在则自动创建默认配置文件
     -d value, --disable value [ -d value, --disable value ]  禁用：禁止特定插件执行，仅支持输入插件名
     -g value, --group value [ -g value, --group value ]      插件组：执行指定的插件组文件
     -r value, --run value [ -r value, --run value ]          仅执行：仅执行指定的插件，支持glob/绝对路径/相对路径
```

## ⚡️ 进阶

下列高级用法请查看 https://docs.xray.cool/tools/xapp/QuickStart 使用。

 - 指纹打分

## 😘 指纹仓库/贡献指纹

访问[xray-plugins](https://github.com/chaitin/xray-plugins)查看详情

## 📝 讨论区

提交误报漏报需求等等请务必先阅读 https://docs.xray.cool/#/guide/feedback

如有问题可以在 GitHub 提 issue, 也可在下方的讨论组里

1. GitHub issue: https://github.com/chaitin/xapp/issues

2. 微信公众号：微信扫描以下二维码，关注我们

    <img src="image/wechat.jpg" height="200px">

3. 微信群: 请添加微信公众号并点击“联系我们" -> "加群“，然后扫描二维码加群

4. QQ 群: 717365081
