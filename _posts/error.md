title: 常见错误代号
id: .nan
categories:
  - HTML
date: 2016-03-09 18:23:53
tags: error
keywords: 梦遥奇缘,PHP,HTML,JS,Linux,YII,YAF,禾子,永远的呆,hexo,github,gitcafe,pacman,Laravel,CodeIgniter
---
## 页面Http状态查询工具说明
1.建议直接Ctrl+F来查找状态码
2.如果向您的服务器发出了某项请求要求显示您网站上的某个网页，那么，您的服务器会返回 HTTP 状态代码以响应该请求。
3.如果向您的服务器发出了某项请求要求显示您网站上的某个网页（例如，当用户通过浏览器访问您的网页或在 Googlebot 抓取该网页时），那么，您的服务器会返回 HTTP 状态代码以响应该请求。
4.此状态代码提供了有关请求状态的信息，且为 Googlebot 提供了有关您网站和请求的网页的信息。
5.一些常见的状态代码为：
200 - 服务器成功返回网页
404 - 请求的网页不存在
503 - 服务器暂时不可用

​
## 1xx（临时响应）

用于表示临时响应并需要请求者执行操作才能继续的状态代码。
代码 说明
100（继续） 请求者应当继续提出请求。服务器返回此代码则意味着，服务器已收到了请求的第一部分，现正在等待接收其余部分。
101（切换协议） 请求者已要求服务器切换协议，服务器已确认并准备进行切换。


## 2xx（成功）

用于表示服务器已成功处理了请求的状态代码。
代码 说明
200（成功） 服务器已成功处理了请求。通常，这表示服务器提供了请求的网页。如果您的 robots.txt 文件显示为此状态，那么，这表示 Googlebot 已成功检索到该文件。
201（已创建） 请求成功且服务器已创建了新的资源。
202（已接受） 服务器已接受了请求，但尚未对其进行处理。
203（非授权信息） 服务器已成功处理了请求，但返回了可能来自另一来源的信息。
204（无内容） 服务器成功处理了请求，但未返回任何内容。
205（重置内容） 服务器成功处理了请求，但未返回任何内容。与 204 响应不同，此响应要求请求者重置文档视图（例如清除表单内容以输入新内容）。
206（部分内容） 服务器成功处理了部分 GET 请求。


## 3xx（已重定向）

要完成请求，您需要进一步进行操作。通常，这些状态代码是永远重定向的。Google 建议您在每次请求时使用的重定向要少于 5 个。您可以使用网站管理员工具来查看 Googlebot 在抓取您已重定向的网页时是否会遇到问题。
代码 说明
300（多种选择） 服务器根据请求可执行多种操作。服务器可根据请求者 (User agent) 来选择一项操作，或提供操作列表供请求者选择。
301（永久移动） 请求的网页已被永久移动到新位置。服务器返回此响应（作为对 GET 或 HEAD 请求的响应）时，会自动将请求者转到新位置。您应使用此代码通知 Googlebot 某个网页或网站已被永久移动到新位置。
302（临时移动） 服务器目前正从不同位置的网页响应请求，但请求者应继续使用原有位置来进行以后的请求。此代码与响应 GET 和 HEAD 请求的 301 代码类似，会自动将请求者转到不同的位置。但由于 Googlebot 会继续抓取原有位置并将其编入索引，因此您不应使用此代码来通知 Googlebot 某个页面或网站已被移动。
303（查看其他位置） 当请求者应对不同的位置进行单独的 GET 请求以检索响应时，服务器会返回此代码。对于除 HEAD 请求之外的所有请求，服务器会自动转到其他位置。
304（未修改） 
自从上次请求后，请求的网页未被修改过。服务器返回此响应时，不会返回网页内容。
如果网页自请求者上次请求后再也没有更改过，您应当将服务器配置为返回此响应（称为 If-Modified-Since HTTP 标头）。由于服务器可以告诉 Googlebot 自从上次抓取后网页没有更改过，因此可节省 带宽和开销
305（使用代理） 请求者只能使用代理访问请求的网页。如果服务器返回此响应，那么，服务器还会指明请求者应当使用的代理。
307（临时重定向） 服务器目前正从不同位置的网页响应请求，但请求者应继续使用原有位置来进行以后的请求。此代码与响应 GET 和 HEAD 请求的 301 代码类似，会自动将请求者转到不同的位置。但由于 Googlebot 会继续抓取原有位置并将其编入索引，因此您不应使用此代码来通知 Googlebot 某个页面或网站已被移动。


## 4xx（请求错误）

这些状态代码表示，请求可能出错，已妨碍了服务器对请求的处理。
代码 说明
400（错误请求） 服务器不理解请求的语法。
401（未授权） 请求要求进行身份验证。登录后，服务器可能会返回对页面的此响应。
403（已禁止） 服务器拒绝请求。如果在 Googlebot 尝试抓取您网站上的有效网页时显示此状态代码（您可在 Google 网站管理员工具中诊断下的网络抓取页面上看到此状态代码），那么，这可能是您的服务器或主机拒绝 Googlebot 对其进行访问。
404（未找到） 
服务器找不到请求的网页。例如，如果请求是针对服务器上不存在的网页进行的，那么，服务器通常会返回此代码。
如然而，如果您有 robots.txt 文件而又发现了此状态，那么，这说明您的 robots.txt 文件可能是命名错误或位于错误的位置。（该文件应当位于顶级域名上，且应当名为 robots.txt）。
如果您在 Googlebot 尝试抓取的网址上发现此状态（位于"诊断"标签的 HTTP 错误页上），那么，这表示 Googlebot 所追踪的可能是另一网页中的无效链接（旧链接或输入有误的链接）。
405（方法禁用） 禁用请求中所指定的方法。
406（不接受） 无法使用请求的内容特性来响应请求的网页。
407（需要代理授权） 此状态代码与 401（未授权）类似，但却指定了请求者应当使用代理进行授权。如果服务器返回此响应，那么，服务器还会指明请求者应当使用的代理。
408（请求超时） 服务器等候请求时超时。
409（冲突） 服务器在完成请求时发生冲突。服务器必须包含有关响应中所发生的冲突的信息。服务器在响应与前一个请求相冲突的 PUT 请求时可能会返回此代码，同时会提供两个请求的差异列表。
410（已删除） 如果请求的资源已被永久删除，那么，服务器会返回此响应。该代码与 404（未找到）代码类似，但在资源以前有但现在已经不复存在的情况下，有时会替代 404 代码出现。如果资源已被永久删除，那么，您应当使用 301 代码指定该资源的新位置。
411（需要有效长度） 服务器不会接受包含无效内容长度标头字段的请求。
412（未满足前提条件） 服务器未满足请求者在请求中设置的其中一个前提条件。
413（请求实体过大） 服务器无法处理请求，因为请求实体过大，已超出服务器的处理能力。
414（请求的 URI 过长） 请求的 URI（通常为网址）过长，服务器无法进行处理。
415（不支持的媒体类型） 请求的格式不受请求页面的支持。
416（请求范围不符合要求） 如果请求是针对网页的无效范围进行的，那么，服务器会返回此状态代码。
417（未满足期望值） 服务器未满足"期望"请求标头字段的要求。


## 5xx（服务器错误）

这些状态代码表示，服务器在尝试处理请求时发生内部错误。这些错误可能是服务器本身的错误，而不是请求出错。

代码 说明
500（服务器内部错误） 服务器遇到错误，无法完成请求。
501（尚未实施） 服务器不具备完成请求的功能。例如，当服务器无法识别请求方法时，服务器可能会返回此代码。
502（错误网关） 服务器作为网关或代理，从上游服务器收到了无效的响应。
503（服务不可用） 目前无法使用服务器（由于超载或进行停机维护）。通常，这只是一种暂时的状态。
504（网关超时） 服务器作为网关或代理，未及时从上游服务器接收请求。
505（HTTP 版本不受支持） 服务器不支持请求中所使用的 HTTP 协议版本。