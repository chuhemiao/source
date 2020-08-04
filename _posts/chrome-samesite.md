title: Chrome 80版本之后为何使用SameSite，cookie隐私和防止CSRF问题如何解决
id: .nan
categories:
  - javascript
date: 2020-08-04 11:59:53
toc: true
tags: 
	- chrome
    - cookie
    - React native
    - HTTPOnly
keywords: 梦遥奇缘,ios,HTTPOnly,JS,typescript,react,SameSite,js,前端开发,安卓打包,ios打包,谷歌浏览器,des,3des
---

### 为什么添加SameSite 

+ cookies面临的两个问题：用户隐私 / CSRF(跨站请求伪造)
+ 明确cookie的使用范围，减少被攻击的可能

### Cookie 的设置步骤

+ 客户端发送 HTTP 请求到服务器
+ 当服务器收到 HTTP 请求时，在响应头里面添加一个 Set-Cookie 字段
+ 浏览器收到响应后保存下 Cookie
+ 之后对该服务器每一次请求中都通过 Cookie 字段将 Cookie 信息发送给服务器。

### cookie的一些属性

![浏览器cookie和same-site](https://i.loli.net/2020/08/03/25vlgEdmMktCwGy.png)

+ Name/Value
	+ 用 JavaScript 操作 Cookie 的时候注意对 Value 进行编码处理。

+ Expires
	+ Expires 用于设置 Cookie 的过期时间。比如：

	+ Set-Cookie: id=a3fWa; Expires=Wed, 21 Oct 2015 07:28:00 GMT;
	+ 当 Expires 属性缺省时，表示是会话性 Cookie，像上图 Expires 的值为 Session，表示的就是会话性 Cookie。当为会话性 Cookie 的时候，值保存在客户端内存中，并在用户关闭浏览器时失效。需要注意的是，有些浏览器提供了会话恢复功能，这种情况下即使关闭了浏览器，会话期 Cookie 也会被保留下来，就好像浏览器从来没有关闭一样。

	+ 与会话性 Cookie 相对的是持久性 Cookie，持久性 Cookies 会保存在用户的硬盘中，直至过期或者清除 Cookie。这里值得注意的是，设定的日期和时间只与客户端相关，而不是服务端。

+ Max-Age
		- Max-Age 用于设置在 Cookie 失效之前需要经过的秒数。比如：
		- Set-Cookie: id=a3fWa; Max-Age=604800;
		- Max-Age 可以为正数、负数、甚至是 0。
		- 如果 max-Age 属性为正数时，浏览器会将其持久化，即写到对应的 Cookie 文件中。
		- 当 max-Age 属性为负数，则表示该 Cookie 只是一个会话性 Cookie。
		- 当 max-Age 为 0 时，则会立即删除这个 Cookie。
		- 假如 Expires 和 Max-Age 都存在，Max-Age 优先级更高。

+ Domain
	+ Domain 指定了 Cookie 可以送达的host。假如没有指定，那么默认值为当前文档访问地址中的主机部分（但是不包含子域名）。
	+ 不能跨域设置 Cookie

+ Path
	+ Path 指定了一个 URL 路径，这个路径必须出现在要请求的资源的路径中才可以发送 Cookie 首部。比如设置 Path=/docs，/docs/Web/ 下的资源会带 Cookie 首部，/test 则不会携带 Cookie 首部。

	+ Domain 和 Path 标识共同定义了 Cookie 的作用域：即 Cookie 应该发送给哪些 URL。

+ Secure属性
	+ 标记为 Secure 的 Cookie 只应通过被HTTPS协议加密过的请求发送给服务端。使用 HTTPS 安全协议，可以保护 Cookie 在浏览器和 Web 服务器间的传输过程中不被窃取和篡改。

+ HTTPOnly
	+ 设置 HTTPOnly 属性可以防止客户端脚本通过 document.cookie 等方式访问 Cookie，有助于避免 XSS 攻击。

+ SameSite
	+ SameSite 是谷歌 2 月份发布的 Chrome80 版本中默认屏蔽了第三方的 Cookie，更大程度的防止跨域之间CSRF和保护用户隐私，借用Token+SameSite形式有效的解决CSRF问题。

### SameSite属性值

+ SameSite属性用来限制第三方 Cookie，减少安全风险，有三个值：
	+ Strict：仅允许一方请求携带 Cookie，即浏览器将只发送相同站点请求的 Cookie，即当前网页 URL 与请求目标 URL 完全一致
	+ Lax：允许部分第三方请求携带 Cookie
	+ None：无论是否跨站都会发送 Cookie

+ Strict
	+ Strict最为严格，完全禁止第三方 Cookie，跨站点时，任何情况下都不会发送 Cookie。换言之，只有当前网页的 URL 与请求目标一致，才会带上 Cookie。
	+ Set-Cookie: CookieName=CookieValue; SameSite=Strict;
+ Lax
	+ Lax规则稍稍放宽，大多数情况也是不发送第三方 Cookie，但是导航到目标网址的 Get 请求除外。
	+ Set-Cookie: CookieName=CookieValue; SameSite=Lax;

+ None
	+ Chrome 计划将Lax变为默认设置(80版本已实施)。这时，网站可以选择显式关闭SameSite属性，将其设为None。不过，前提是必须同时设置Secure属性（Cookie 只能通过 HTTPS 协议发送），否则无效。
	+ Set-Cookie: widget_session=abc123; SameSite=None; Secure


### SameSite影响

![samesite.png](https://i.loli.net/2020/08/03/xtH5pQylGW84bj3.png)

+ 从上图可以看出，对大部分 web 应用而言，Post 表单，iframe，AJAX，Image 这四种情况从以前的跨站会发送三方 Cookie，变成了不发送。

+ Post表单：应该的，学 CSRF 总会举表单的例子。

+ iframe：iframe 嵌入的 web 应用有很多是跨站的，都会受到影响。

+ AJAX：可能会影响部分前端取值的行为和结果。

+ Image：图片一般放 CDN，大部分情况不需要 Cookie，故影响有限。但如果引用了需要鉴权的图片，可能会受到影响。


### 解决方案

+ 临时方案可设置 SameSite 为 None，必须同时设置Secure属性 （Set-cookie: key=value; SameSite=None; Secure）

+ 合理的解决方案简单总结应该是按照谷歌浏览器规则:
	+ 默认设置 SameSite=Lax ，需要第三方cookie的则设置为none，CSRF Token会话类Cookies设置Strict（添加SameSite就是为了防止CSRF攻击）

![netflix默认设置SameSite值为Lax](https://i.loli.net/2020/08/03/TwNmZu9JD78SxWX.png)
	
+ Notice：HTTP 接口不支持 SameSite=none，UA 检测，部分浏览器不能加 SameSite=none
+ [浏览器识别UA能否添加SameSite](https://www.chromium.org/updates/same-site/incompatible-clients)

### 新版本的chrome浏览器（80版本之后），7月14后灰度测试，7月28基本覆盖大部分chrome用户

+ 7月14日稳定发布Chrome 84的同时恢复SameSite Cookie的强制实施，同时对Chrome 80+启用强制实施。

+ cookie的校验更加严格，SameSite属性默认值由None变为Lax
### same-site版本更新说明和讨论

+ [SameSite Updates Version](https://www.chromium.org/updates/same-site)
+ [New cross-site cookie not 'SameSite' warning ](https://github.com/google/google-api-javascript-client/issues/561)
+ [浏览器系列之 Cookie 和 SameSite 属性](https://github.com/mqyqingfeng/Blog/issues/157)
+ [阮一峰：Cookie 的 SameSite 属性](https://www.ruanyifeng.com/blog/2019/09/cookie-samesite.html)