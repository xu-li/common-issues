专业版PAGE应用开发
========

该文档仅适用于新浪微博企业版应用。即在[这里创建](http://open.weibo.com/apps/new?sort=enterprise)的应用。

对于把专业版应用当普通应用处理的(可以这么做的)，请略过。

该文档仅仅是个人的经验分享，不承担任何可能导致的后果。

术语
====

1. **APP_ID/APP_KEY**: OAuth相关的值，可以在[管理页面](http://open.weibo.com/apps)找到你的应用->应用信息->基本信息中找到。
2. **APP_SECRET**: OAuth相关的值，可以在[管理页面](http://open.weibo.com/apps)找到你的应用->应用信息->基本信息中找到。
3. **SUB_APPKEY**: 所有需要使用APP_KEY的地方，都用这个KEY来代替，**除了**跳转。
4. **SUB_SECRET**: 没有这个东西，跟SUB_APPKEY对应的就是APP_SECRET

FAQ
====

Q：使用官方的[授权窗口例子](http://open.weibo.com/wiki/%E4%B8%93%E4%B8%9A%E7%89%88%E5%BA%94%E7%94%A8%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%97)，出现**redirect_uri_mismatch**

A：对于企业版应用，可以在[基本信息](http://open.weibo.com/apps/YOUR_APP_KEY/info/basic)中，设置*安全域名*为*e.weibo.com*。同时，把[高级信息](http://open.weibo.com/apps/YOUR_APP_KEY/info/advanced)中的*授权回调页*置空。

Q：使用官方的[授权窗口例子](http://open.weibo.com/wiki/%E4%B8%93%E4%B8%9A%E7%89%88%E5%BA%94%E7%94%A8%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%97)，授权结束以后，跳转不到自己的APP TAB。

A：可能是*redirect_uri*设置错误。应该设置*http://e.weibo.com/CID_FROM_URL/app_APP_KEY*. 这里的*CID_FROM_URL*就是新浪自动传给IFRAME的参数，被访问者uid。APP_KEY，不是SUB_APPKEY。     




