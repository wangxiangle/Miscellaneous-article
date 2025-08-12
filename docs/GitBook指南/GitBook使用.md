# GitBook基础指南

以下是GitBook项目部署的完整指南，基于行业主流实践整理：

### 一、环境准备（开发端）

1. **Node.js安装**  
   
   - 必须使用v10.x版本（高版本存在兼容性问题）  
   
   - 推荐v10.24.1（官网最新版可能不兼容）
     
     ```bash
     # Linux示例（CentOS）
     wget https://nodejs.org/dist/v10.24.1/node-v10.24.1-linux-x64.tar.xz
     tar xvf node-v10.24.1-linux-x64.tar.xz
     mv node-v10.24.1-linux-x64 /usr/local/
     ln -s /usr/local/node-v10.24.1-linux-x64/bin/node /usr/bin/node
     ln -s /usr/local/node-v10.24.1-linux-x64/bin/npm /usr/bin/npm
     ```

2. **GitBook安装**  
   
   ```bash
   npm install -g gitbook-cli  # 安装命令行工具
   gitbook -V  # 验证安装（自动下载所需版本）
   ```

### 二、网站构建流程

```bash
gitbook init    # 初始化书籍目录
gitbook build   # 生成_book静态网站目录


//生成电子书格式
gitbook epub .
gitbook mobi .    
gitbook pdf .
```

### 三、部署方案

#### 1. GitHub Pages（推荐）

```bash
# 创建gh-pages分支
git checkout --orphan gh-pages
git rm -rf .
cp -rf _book/* .
git add .
git commit -m "Deploy GitBook"
git push -u origin gh-pages
```

- 仓库设置中开启GitHub Pages服务  
- 访问地址：`https://<用户名>.github.io/<仓库名>`

#### 2. 自有服务器部署（Linux）

```bash
# 上传文件
rsync -avz _book/ user@server:/var/www/html/gitbook

# Nginx配置示例
server {
  listen 80;
  server_name docs.yourdomain.com;
  root /var/www/html/gitbook;
  index index.html;
}
```

#### 3. 云存储方案

- **腾讯云COS**  
  开启静态网站托管功能，上传`_book`目录  
- **阿里云OSS**  
  配置Bucket为静态网站托管模式

### 四、高级部署方案

#### 1. 持续集成部署

```yml
# GitHub Actions示例
name: Deploy GitBook
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Setup Node v10
      uses: actions/setup-node@v3
      with: { node-version: '10.x' }
    - run: npm install -g gitbook-cli
    - run: gitbook build
    - name: Deploy to GH Pages
      uses: peaceiris/actions-gh-pages@v3
      with: 
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./_book
```

#### 2. 内网穿透方案（本地调试）

1. 启动本地服务：
   
   ```bash
   gitbook serve  # 默认端口4000
   ```

2. 使用内网穿透工具：
   
   - [路由侠](https://www.luyouxia.com)映射4000端口
   - Ngrok/FRP等工具

### 五、注意事项

1. 国内环境安装需配置淘宝镜像：
   
   ```bash
   npm config set registry https://registry.npmmirror.com
   ```

2. 文件权限问题（Linux部署）：
   
   ```bash
   chown -R www-data:www-data /var/www/html/gitbook
   ```

3. 版本兼容性：
   
   - 避免使用Node.js v12+版本  
   - GitBook插件需与版本匹配

> [!TIP]
> GitBook官方服务需代理访问，建议优先选择静态部署方案。完整文档模板参考[GitBook官方示例](https://github.com/GitbookIO/gitbook)。

引用链接：
1.[gitbook使用教程 - CSDN博客](https://blog.csdn.net/weixin_34248023/article/details/88674884)
2.[GitBook部署指南-CSDN博客 - CSDN博客](https://blog.csdn.net/fwhezfwhez/article/details/86756036)
3.[GitBook安装使用笔记(一)安装部署 - 腾讯云](https://cloud.tencent.com/developer/article/2127648)
4.[GitBook安装部署实操手册 - 非著名野生程序员 - 博客园 - 博客园](https://www.cnblogs.com/yurunmiao/p/12342131.html)
5.[本地部署命令行工具 GitBook 并实现外部访问 - 路由侠](https://help.luyouxia.com/?p=7850)
6.[GitBook安装部署实操手册 - 散修工程师](https://zhuanlan.zhihu.com/p/108276695)
7.[私有GitBook服务部署说明 - 博客园](https://www.cnblogs.com/student-luo/p/15250176.html)
8.[Gitbook超详细使用教程,搭建属于你自己的博客! - CSDN博客](https://blog.csdn.net/xf555er/article/details/132418146)
9.[GitBook客户端:跨平台技术文档协作工具 - CSDN博客](https://blog.csdn.net/weixin_36074800/article/details/143929248)
10.[【Github】神奇的文档网站项目,零成本部署个人站点 - 哔哩哔哩](http://www.bilibili.com/video/BV1LCgWzqEK9)
11.[快速部署个人主页!vite项目前端如何手动部署至Github上展示 - 哔哩哔哩](http://www.bilibili.com/video/BV1hp3izYESc)
12.[手把手教你用GitHub部署一个你的网站(有网址的哦) - 哔哩哔哩](http://www.bilibili.com/video/BV1tvh8zfEux)
13.[一文教你使用 Gitbook 部署电子书到云端 - 腾讯云](https://cloud.tencent.com/developer/article/1961083)
14.[使用Gitbook 打造你的电子书 - 慕课网](https://zhuanlan.zhihu.com/p/34946169)
15.[使用Git进行控制,并把项目托管到 GitBook.com(二) - 博客园](https://www.cnblogs.com/lydms/p/12921513.html)
16.[GitBook 入门指南 - 王虾片](https://zhuanlan.zhihu.com/p/343212233)
17.[Win 10下gitbook本地部署过程及问题处理 - CSDN博客](https://blog.csdn.net/kewaqi618/article/details/128778736)
18.[使用Hugo+Gitbook+Nginx 构建静态博客网站 - Wayne](https://zhuanlan.zhihu.com/p/268922834)
19.[GitBook在Windows下安装部署 - CSDN博客](https://blog.csdn.net/annita2019/article/details/108888381)
20.[Gitbook 小书-快速创建你的个人专栏 - 松桑的前端后花园](http://zhuanlan.zhihu.com/p/690055436)
21.[Gitbook的安装和部署 - 博客园](https://www.cnblogs.com/HappyTeemo/p/17114141.html)
