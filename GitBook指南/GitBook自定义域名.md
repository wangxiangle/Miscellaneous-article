# GitBook自定义域名

### 🔧 一、GitBook平台配置

1. **进入空间设置**  
   登录GitBook后，选择目标Space → 左侧菜单点击 **"Advance"** → 找到 **"Custom Domain"** 模块点击 **"Configure"**。

2. **输入域名**  
   在弹出的对话框中填写你的自定义二级域名（如 `docs.yourdomain.com`），点击 **"Next"**。

### 🌐 二、域名解析配置（以阿里云为例）

1. **添加CNAME记录**  
   在域名服务商控制台：
   
   - **记录类型**：选择 `CNAME`  
   - **主机记录**：填写二级域名前缀（如 `docs`）  
   - **记录值**：固定填写 `hosting.gitbook.io`  
   - TTL：默认10分钟即可  

2. **启用解析**  
   保存后需**手动启用解析规则**（部分服务商需额外点击启用按钮）。

### ✅ 三、验证生效

完成配置后，GitBook会显示 **"Domain configured successfully"** 提示。解析生效通常需10-30分钟，通过浏览器访问自定义域名即可查看电子书。

> ️ **注意事项**  
> 
> - 仅支持绑定**二级域名**（如 `docs.example.com`），不支持顶级域名直接绑定  
> - 若使用国内域名且部署在中国大陆服务器，需完成**ICP备案**  
> - 旧版GitBook（legacy.gitbook.com）与新版本配置独立，新版官网访问需网络工具支持  

[GitBook官方域名配置指南](https://docs.gitbook.com/editing-content/space-settings/custom-domain)（需网络工具访问）

引用链接：
1.[gitbook 域名设置 域名绑定 自定义域名 - CSDN博客](https://blog.csdn.net/u011149152/article/details/139340255)
2.[gitbook图书绑定自定义的域名要怎样做? - 百度经验](https://jingyan.baidu.com/article/335530daf86c3b19cb41c3f3.html)
3.[gitbook 入门教程之使用 gitbook.com 在线开发电子书 - 博客园](https://www.cnblogs.com/snowdreams1006/p/10657647.html)
4.[GitBook 进阶篇之搭建博客 - CSDN博客](https://blog.csdn.net/young2415/article/details/113782741)
5.[gitbook 入门教程之使用 gitbook.com 在线开发电子书  - 腾讯云](https://cloud.tencent.com/developer/article/1414738)
6.[使用GitBook将文档型项目仓库发布为在线电子书 - 51CTO学堂](https://edu.51cto.com/article/note/38312.html)
7.[gitbook怎么用 - 太平洋科技](https://g.pconline.com.cn/x/1947/19477170.html)
8.[Gitbook超详细使用教程,搭建属于你自己的博客! - CSDN博客](https://blog.csdn.net/xf555er/article/details/132418146)
9.[GitBook – The complete API documentation tool  - www.gitbook.com](https://www.gitbook.com/solutions/api)
10.[一文教你使用 Gitbook 部署电子书到云端 - 腾讯云](https://cloud.tencent.com/developer/article/1961083)
11.[Gitbook 小书-快速创建你的个人专栏 - CSDN博客](https://blog.csdn.net/weixin_43303603/article/details/137210189)
12.[使用Gitbook 打造你的电子书 - 慕课网](https://zhuanlan.zhihu.com/p/34946169)
13.[技术资料平台 gitbook - 毫末科技](https://haomo-tech.com/haomotraining/materials/3.platform/gitbook.html)
14.[62K Star!这款GitHub项目可免费无实名注册域名,这你能信?已20万+人亲测能用! - 知乎](http://zhuanlan.zhihu.com/p/1921746560682819697)
15.[Gitbook 小书-快速创建你的个人专栏 - 松桑的前端后花园](http://zhuanlan.zhihu.com/p/690055436)
16.[GitHub学习教程 | GitHub Pages自定义域名配置指南:从购买到HTTPS启用  - 微信公众平台](https://mp.weixin.qq.com/s?__biz=MzU1NjEwMTY0Mw==&mid=2247600760&idx=1&sn=31e9de98d415950b620392f04e0462bf&chksm=fa1366a212453bdee305ff695a59f21c3838755bccf03e724dd9bf37190be60df01312844512&scene=27)
17.[小白学网站部署,手把手教你,Github Pages 如何自定义域名 - 柒崽](http://zhuanlan.zhihu.com/p/1886365022571176637)
18.[GitBook Documentation - docs.gitbook.com](https://docs.gitbook.com/)
19.[GitBook – Build product documentation your users will love - gitbook.com](https://gitbook.com/)
20.[在GitHub上部署个人网页并设置自定义域名 - 百度开发者中心](https://developer.baidu.com/article/details/2760836)
21.[小乌龟git设置用户名和密码 - 码农星球](http://haokan.baidu.com/v?pd=wisenatural&vid=3545049436455008233)
22.[从0到1,手把手教Git配置使用。软件安装、账户配置(ssh)秘钥、检出代码、配置IntelliJ IDEA、提交代码、拉取代码、合并分支、对比代码、界面UI - 哔哩哔哩](http://www.bilibili.com/video/BV1idHUeLECY)
23.[Gitbook配置教程,快速搭建个人博客,制作个人电子书、帮助(说明)文档 - C语言实验室](http://zhuanlan.zhihu.com/p/693781943)
24.[使用gitbook简单构建你的博客、文档页面  - 掘金开发者社区](https://juejin.cn/post/7385747507953745958)
25.[你觉得 GitBook 体验如何? - 松桑的前端后花园](https://www.zhihu.com/question/26607715/answer/3450103898)
26.[GitBook安装、配置、制作电子书(一) - 51CTO博客](https://blog.51cto.com/u_14883832/6469582)
27.[gitbook 入门教程之网站域名备案 icp 插件 - CSDN博客](https://blog.csdn.net/weixin_38171180/article/details/103637816)
