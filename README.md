***本项目简单食用方法(Windows OS)：***

1. 下载 <a href="https://git-scm.com/downloads">Git</a> <具体安装步骤这里不多讲述,鼠标右键可以看到Git Bash Here 就行>

2. 下载<a href="https://nodejs.org/en/download/">node.js</a><具体安装步骤这里不多讲述,cmd下npm -v有输出就行>

3. 创建一个存放你博客的文件夹，进入文件夹，右键选择 Git Bash Here，然后设置npm的镜像源为淘宝镜像源，这样能**加快下载插件速度**

   ```shell
   npm config set registry https://registry.npm.taobao.org
   ```

4. 在你的博客文件夹下,右键选择 Git Bash Here，然后

   ```shell
   git clone git@github.com:axh2018/hexo_blog.git   .
   npm i
   ```

5. 测试下是否能跑起来

   ```shell
   hexo clean && hexo g && hexo s
   ```

   就可以本地预览了 

   * <a href="https://axh2018.github.io/">点击预览</a>

   > hexo  clean (清除缓存文件,可简写hexo cl)

   > hexo generate (生成网页,可简写hexo g)

   > hexo server (本地预览,可简写hexo s)

   > hexo deploy (部署到GitHub,可简写hexo d)


6. 能跑起来的话，就可以把相关信息该为自己的然后部署到GitHub上了，Github创建一个仓库，这个仓库的名字必须是 userid.github.io ,例如我的id是axh2018，那么我的仓库名就必须是axh2018.github.io 

   hexo主题用的是[matery]( https://github.com/blinkfox/hexo-theme-matery )

   matery主题的优点:

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

  本项目已集成以下插件:

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

值得注意的是，您需要把相关的个人信息改为您自己的信息，这其中包括一些插件的id，您需要自行去注册，然后修改_config.yaml文件里与之相应的id
