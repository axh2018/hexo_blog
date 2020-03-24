

### 简单开始：

1. 下载 <a href="https://git-scm.com/downloads">Git</a> <鼠标右键可以看到`Git Bash Here` 即可>

   

2. 下载<a href="https://nodejs.org/en/download/">node.js</a><`cmd`下`npm -v`有输出即可>

   

3. 配置镜像源

   创建一个存放你博客的文件夹，进入文件夹，右键选择 `Git Bash Here`，然后设置`npm`的镜像源为淘宝镜像源，这样能**加快下载插件速度**

   ```shell
   $ npm config set registry https://registry.npm.taobao.org
   ```

4. 配置`git`账户和邮箱
      在你的博客文件夹下右键`Git Bash Here`

      **这里的账号和邮箱换成你自己的**
      
      ```shell script
      $ git config --global user.name "GithubID" 
$ git config --global user.email "email-address"
      ```

5. 生成密钥(这里三次回车)

      **邮箱同样换成自己的**

      ```shell
      $ ssh-keygen -t rsa -C "email-address"
      ```

6. 密钥上传到`Github`

   ````shell script
    $ cat ~/.ssh/id_rsa.pub
   ````
   到`GitHub`网站上点右上角`Settings,SSH and GPG Keys`,新建一个`key`,将上面的结果复制填进去即可

7. 测试是否上传成功

      下面的指令的输出能看到你Github账户名字即可

      ````shell script
      $ ssh -T git@github.com
      ````

8. 克隆项目

   在你的博客文件夹下,右键选择 `Git Bash Here`，然后

   ```shell
   $ git clone git@github.com:axh2018/hexo_blog.git  .  #克隆项目
   $ npm i							 #安装相关依赖插件和框架
   ```

9. 测试是否正常预览

   ```shell
   $ hexo clean && hexo g && hexo s
   ```

   打开浏览器输入127.0.0.1:4000即可本地预览效果

   <a href="https://axh2018.github.io/">点击预览https://axh2018.github.io/</a>

   > hexo  clean (清除缓存文件,可简写hexo cl)

   > hexo generate (生成网页,可简写hexo g)

   > hexo server (本地预览,可简写hexo s)

   > hexo deploy (部署到GitHub,可简写hexo d)


6. 能本地预览，就可以把相关信息改为自己的然后部署到`GitHub`上
   `Github`创建一个仓库，这个仓库的名字必须是 `userid.github.io `
   例如我的`id`是`axh2018`，那么我的仓库名就必须是`axh2018.github.io `
   
7. `Hexo`部署到`Github`,修改你博客文件夹根目录下的`_config.yml`文件的倒数第二行,repository的地址改成你的`GitHub`博客仓库地址
````shell script
deploy:
  type: git
  repository: https://github.com/axh2018/axh2018.github.io
  branch: master
````
**到这基本就完成了，剩下你所需要的工作就是把配置文件(根目录下的_config.yml和主题文件夹下的_config_yml)的相关信息改为你自己的信息即可。**

* 写文章直接在你的博客文件夹下右键`Git Bash Here`
````shell script
$ hexo new post "第一篇文章"
````
然后根目录下的`source`文件夹里会有一个"第一篇文章.md"文件
你只需要编辑这个`md`文件就行啦,什么?什么是`md`文件?
`md`即`MarkDown`文件的后缀名

>Markdown是一种可以使用普通文本编辑器编写的标记语言
>通过简单的标记语法,它可以使普通文本内容具有一定的格式
>Markdown具有一系列衍生版本,用于扩展Markdown的功能(如表格、脚注、内嵌HTML等等)
>这些功能原初的Markdown尚不具备，它们能让Markdown转换成更多的格式
>例如LaTeX，Docbook。Markdown增强版中比较有名的有Markdown Extra、MultiMarkdown、 Maruku等
>这些衍生版本要么基于工具，如Pandoc；要么基于网站，如GitHub和Wikipedia
>在语法上基本兼容，但在一些语法和渲染效果上有改动。

编辑`MarkDown`文件,安利一下<a href="https://typora.io/">typora</a>这款软件,或者<a href="https://visualstudio.microsoft.com/zh-hans/?rr=https%3A%2F%2Fcn.bing.com%2F">Visual Studio</a>这款强大的`IDE`

   **hexo主题用的是[matery]( https://github.com/blinkfox/hexo-theme-matery )**
   **matery主题的优点:**

- 简单漂亮，文章内容美观易读
- [Material Design](https://material.io/) 设计
- 响应式设计，博客在桌面端、平板、手机等设备上均能很好的展现
- 首页轮播文章及每天动态切换 `Banner` 图片
- 瀑布流式的博客文章列表（文章无特色图片时会有 `24` 张漂亮的图片代替）
- 时间轴式的归档页
- **词云**的标签页和**雷达图**的分类页
- 丰富的关于我页面（包括关于我、文章统计图、我的项目、我的技能、相册等）
- 可自定义的数据的友情链接页面
- 支持文章置顶和文章打赏
- 支持 `MathJax`
- `TOC` 目录
- 可设置复制文章内容时追加版权信息
- 可设置阅读文章时做密码验证
- [Gitalk](https://gitalk.github.io/)、[Gitment](https://imsun.github.io/gitment/)、[Valine](https://valine.js.org/) 和 [Disqus](https://disqus.com/) 评论模块（推荐使用 `Gitalk`）
- 集成了[不蒜子统计](http://busuanzi.ibruce.info/)、谷歌分析（`Google Analytics`）和文章字数统计等功能
- 支持在首页的音乐播放和视频播放功能
- 支持`emoji`表情，用`markdown emoji`语法书写直接生成对应的能**跳跃**的表情。
- 支持 [DaoVoice](http://www.daovoice.io/)、[Tidio](https://www.tidio.com/) 在线聊天功能。

  **本项目已集成以下插件:**

- 添加emoji表情支持
- 代码高亮
- hexo-generator-search
- 中文拼音转链接
- 文章字数统计
- 添加RSS订阅
- DaoVoice在线聊天功能
- Tidio在线聊天功能
- Crisp在线聊天工具
- 天气插件
- 外链跳转插件
- 鼠标点击爆炸效果
- 樱花飘落效果
- 文章生成永久链接
- Gitalk评论模块
- 网页图片懒加载
