# How to build our own websites with Hugo on Windows?

<!--more-->

## Build our own website by using Hugo on Wins


## Install Hugo

There are so many tutorials for installing hugo on macOS and Linux, and this blog mainly fucuses on how to install hugo on Windows.

And I recommend using method two.

### Method One： Using Official Docs

Hugo official installation file：

[Install Hugo | Hugo (gohugo.io)](https://gohugo.io/getting-started/installing/)

First, make sure you have chocolatey on your laptop with Windows system.

#### 1. Install chocolatey on Windows

[Chocolatey Software Docs | Setup / Install](https://docs.chocolatey.org/en-us/choco/setup#more-install-options)

> Please remember to start a command prompt as an administrator.

run the following command:

```bash
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

Check whether hugo is installed successfully with the following command:

```bash
choco help
```

2.Install Hugo with Chocolatey

If you are on a Windows machine and use [Chocolatey](https://chocolatey.org/) for package management, you can install Hugo with the following one-liner:

install-with-chocolatey.ps1

```bash
choco install hugo -confirm
```

Or if you need the “extended” Sass/SCSS version:

install-extended-with-chocolatey.ps1

```bash
choco install hugo-extended -confirm
```

### Method Two：Download hugo.exe directly

#### 1.Download Hugo

[Releases · gohugoio/hugo (github.com)](https://github.com/gohugoio/hugo/releases)

> Download the certain version you need. Some website themes have requirements of hugo version.

#### 2. Set Environment Variables

Set the folder of hugo.exe as environment variables.

Then, open another command line to check whether it is successfully set or not.  Run the command in CMD:

hugo version

## Themes I Prefered

There are many themes on the official websites.

[Complete List | Hugo Themes (gohugo.io)](https://themes.gohugo.io/)

Personally I prefered the following themes.

[Academic | Hugo Themes (gohugo.io)](https://themes.gohugo.io/themes/hugo-academic/)

[Academic | Hugo Themes (gohugo.io)](https://themes.gohugo.io/themes/hugo-academic/)

[PaperMod | Hugo Themes (gohugo.io)](https://themes.gohugo.io/themes/hugo-papermod/)

[Even | Hugo Themes (gohugo.io)](https://themes.gohugo.io/themes/hugo-theme-even/)

[Tranquilpeak | Hugo Themes (gohugo.io)](https://themes.gohugo.io/themes/hugo-tranquilpeak-theme/)

[Clean White | Hugo Themes (gohugo.io)](https://themes.gohugo.io/themes/hugo-theme-cleanwhite/)

[LoveIt | Hugo Themes (gohugo.io)](https://themes.gohugo.io/themes/loveit/)

I use the theme LoveIt.

[LoveIt (hugoloveit.com)](https://hugoloveit.com/zh-cn/)

Install it according to the official document and try to build demo yourself.

[Theme Documentation - Basics - LoveIt (hugoloveit.com)](https://hugoloveit.com/theme-documentation-basics/)

You can also follow the steps in this video. Although it is on the MacOS system, she explained everything clearly in Chinese.

[Hugo - 10分钟搭建 & 部署个人网站/博客，简历中的博客网站怎么建*哔哩哔哩*bilibili](https://www.bilibili.com/video/BV1x64y117PX?from=search&seid=16183394120919000097&spm_id_from=333.337.0.0)

{{< bilibili id=BV1x64y117PX >}}

## Memos

### Important Command

#### 1.hugo serve

Execute`hugo serve` under the root folder of the project,  click http://localhost:1313/ to visit your website locally.

#### 2.hugo

- make sure that in the config.toml , it  is written like baseUrl="https://[username].github.io"
- Execute`hugo` under the root folder of the project. For the first time you do it,  the `public` folder will be made.  If there is any mistake when compiling, it is recomended to delete all files in the `public` folder before execute `hugo`.

### Publish on GitHub Pages

- new a repository，setting it to public。
- Set the address of your blog `[username].github.io` at setting/pages. Set the branch to master if you use it.
- Execute`hugo` under the root folder of the project. For the first time you do it,  the `public` folder will be made.(make sure that in the config.toml , it  is written like baseUrl="https://[username].github.io")

  `cd public`, run the command:

  ```
  git init
  git add .
  git commit -m"first commit"
  git add remote origin "your reposotory address"
  git push -u origin master
  ```

Wait a few minites，and you can visit your website on `https://[username].github.io`.

tips:

> If the your website doesn't change after a sucessful push, please check the `actions` of repository. The compiling of new github pages probably failed.

> If there is any mistake when compiling, it is recomended to delete all files in the `public` folder before execute `hugo`.

### Some mistakes I met

If the style/css of the website went wrong, you should check the url and address in index.html page. Perhaps the baseUrl is wrong.

### The Extended Functions of LoveIt：

[Hugo系列(3.0) - LoveIt主题美化与博客功能增强 · 第一章 - Yulin Lewis' Blog (lewky.cn)](https://lewky.cn/posts/hugo-3.html/#添加自定义的_customscss)

There are four blogs in the link , including the improvements of  searching！

The official link is also helpful.

[Theme Documentation - Extended Shortcodes - LoveIt (hugoloveit.com)](https://hugoloveit.com/theme-documentation-extended-shortcodes/)

#### Save My config.toml

I revise the config.toml according to the offical demo and files,

including:

```
   
      [params.header.title]
      # LOGO 的 URL
      logo = ""
      # 标题名称
      name = "xxx"
  
      [params.home.profile]
      enable = true
      # Gravatar 邮箱，用于优先在主页显示的头像
      gravatarEmail = ""
      # 主页显示头像的 URL
      avatarURL = "/images/avatar.png"
      #  主页显示的网站标题 (支持 HTML 格式)
      title = "xxx"
      # 主页显示的网站副标题
      subtitle = "这是我的全新 Hugo 网站"
  
      #  是否保持使用文章前面的静态目录
      keepStatic = false
  
    [params.list]
    # list 页面每页显示文章数量
    paginate = 10
    ...
```

Here is my config.toml

I delete the function of comments, because it goes wrong on github pages.

```
baseURL = "https://xxx.github.io/"
# [en, zh-cn, fr, ...] determines default content language
defaultContentLanguage = "en"
# language code
languageCode = "en"
title = "xxx's blog"

# Change the default theme to be use when building the site with Hugo
theme =  ["hugo-search-fuse-js","LoveIt"]


# whether to use emoji code
# 是否使用 emoji 代码
enableEmoji = true


[menu]
  [[menu.main]]
    identifier = "posts"
    # you can add extra information before the name (HTML format is supported), such as icons
    pre = ""
    # you can add extra information after the name (HTML format is supported), such as icons
    post = ""
    name = "Posts"
    url = "/posts/"
    # title will be shown when you hover on this menu link
    title = ""
    weight = 1
  [[menu.main]]
    identifier = "projects"
    # you can add extra information before the name (HTML format is supported), such as icons
    pre = ""
    # you can add extra information after the name (HTML format is supported), such as icons
    post = ""
    name = "Projects"
    url = "/categories/projects/"
    # title will be shown when you hover on this menu link
    title = ""
    weight = 1
  [[menu.main]]
    identifier = "tags"
    pre = ""
    post = ""
    name = "Tags"
    url = "/tags/"
    title = ""
    weight = 2
  [[menu.main]]
    identifier = "categories"
    pre = ""
    post = ""
    name = "Categories"
    url = "/categories/"
    title = ""
    weight = 3
  [[menu.main]]
    identifier = "about"
    pre = ""
    post = ""
    name = "About"
    url = "/about/"
    title = ""
    weight = 5
  [[menu.main]]
    pre = "<i class='fas fa-fw fa-search'></i>"
    name = "search"
    weight = 7
    identifier = "search"
    url = "/search/"


[params]
  #  LoveIt 主题版本
  version = "0.2.X"
  # 网站描述
  description = "这是我的全新 Hugo 网站"
  # 网站关键词
  keywords = ["Theme", "Hugo"]
  # 网站默认主题样式 ("light", "dark", "auto")
  defaultTheme = "auto"
  # 公共 git 仓库路径，仅在 enableGitInfo 设为 true 时有效
  gitRepo = ""
  #  哪种哈希函数用来 SRI, 为空时表示不使用 SRI
  # ("sha256", "sha384", "sha512", "md5")
  fingerprint = ""
  #  日期格式
  dateFormat = "2006-01-02"
  # 网站图片, 用于 Open Graph 和 Twitter Cards
  images = ["/logo.png"]

  #  应用图标配置
  [params.app]
    # 当添加到 iOS 主屏幕或者 Android 启动器时的标题, 覆盖默认标题
    title = "LoveIt"
    # 是否隐藏网站图标资源链接
    noFavicon = false
    # 更现代的 SVG 网站图标, 可替代旧的 .png 和 .ico 文件
    svgFavicon = ""
    # Android 浏览器主题色
    themeColor = "#ffffff"
    # Safari 图标颜色
    iconColor = "#5bbad5"
    # Windows v8-10磁贴颜色
    tileColor = "#da532c"

  #  搜索配置
  [params.search]
    enable = false
    # 搜索引擎的类型 ("lunr", "algolia")
    type = "lunr"
    # 文章内容最长索引长度
    contentLength = 4000
    # 搜索框的占位提示语
    placeholder = ""
    #  最大结果数目
    maxResultLength = 10
    #  结果内容片段长度
    snippetLength = 50
    #  搜索结果中高亮部分的 HTML 标签
    highlightTag = "em"
    #  是否在搜索索引中使用基于 baseURL 的绝对路径
    absoluteURL = false
    [params.search.algolia]
      index = ""
      appID = ""
      searchKey = ""

  # 页面头部导航栏配置
  [params.header]
    # 桌面端导航栏模式 ("fixed", "normal", "auto")
    desktopMode = "fixed"
    # 移动端导航栏模式 ("fixed", "normal", "auto")
    mobileMode = "auto"
    #  页面头部导航栏标题配置
    [params.header.title]
      # LOGO 的 URL
      logo = ""
      # 标题名称
      name = "Isaray's blog"
      # 你可以在名称 (允许 HTML 格式) 之前添加其他信息, 例如图标
      pre = ""
      # 你可以在名称 (允许 HTML 格式) 之后添加其他信息, 例如图标
      post = ""
      #  是否为标题显示打字机动画
      typeit = false

  # 页面底部信息配置
  [params.footer]
    enable = true
    #  自定义内容 (支持 HTML 格式)
    custom = ''
    #  是否显示 Hugo 和主题信息
    hugo = true
    #  是否显示版权信息
    copyright = true
    #  是否显示作者
    author = true
    # 网站创立年份
    since = 2019
    # ICP 备案信息，仅在中国使用 (支持 HTML 格式)
    icp = ""
    # 许可协议信息 (支持 HTML 格式)
    license = '<a rel="license external nofollow noopener noreffer" href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank">CC BY-NC 4.0</a>'

  #  Section (所有文章) 页面配置
  [params.section]
    # section 页面每页显示文章数量
    paginate = 10
    # 日期格式 (月和日)
    dateFormat = "01-02"
    # RSS 文章数目
    rss = 10

  #  List (目录或标签) 页面配置
  [params.list]
    # list 页面每页显示文章数量
    paginate = 10
    # 日期格式 (月和日)
    dateFormat = "01-02"
    # RSS 文章数目
    rss = 10

  # 主页配置
  [params.home]
    #  RSS 文章数目
    rss = 10
    # 主页个人信息
    [params.home.profile]
      enable = true
      # Gravatar 邮箱，用于优先在主页显示的头像
      gravatarEmail = ""
      # 主页显示头像的 URL
      avatarURL = "/images/avatar.png"
      #  主页显示的网站标题 (支持 HTML 格式)
      title = "xxx"
      # 主页显示的网站副标题
      subtitle = "A student major in Data Science and Engineering."
      # 是否为副标题显示打字机动画
      typeit = true
      # 是否显示社交账号
      social = true
      #  免责声明 (支持 HTML 格式)
      disclaimer = ""
    # 主页文章列表
    [params.home.posts]
      enable = true
      # 主页每页显示文章数量
      paginate = 6
      #  被 params.page 中的 hiddenFromHomePage 替代
      # 当你没有在文章前置参数中设置 "hiddenFromHomePage" 时的默认行为
      defaultHiddenFromHomePage = false

  # 作者的社交信息设置
  [params.social]
    GitHub = "https://github.com/Isaray"
    Linkedin = "xxxx"
    Twitter = ""
    Instagram = "xxxx"
    Facebook = ""
    Telegram = "xxxx"
    Medium = ""
    Gitlab = ""
    Youtubelegacy = ""
    Youtubecustom = ""
    Youtubechannel = ""
    Tumblr = ""
    Quora = ""
    Keybase = ""
    Pinterest = ""
    Reddit = ""
    Codepen = ""
    FreeCodeCamp = ""
    Bitbucket = ""
    Stackoverflow = ""
    Weibo = ""
    Odnoklassniki = ""
    VK = ""
    Flickr = ""
    Xing = ""
    Snapchat = ""
    Soundcloud = ""
    Spotify = ""
    Bandcamp = ""
    Paypal = ""
    Fivehundredpx = ""
    Mix = ""
    Goodreads = ""
    Lastfm = ""
    Foursquare = ""
    Hackernews = ""
    Kickstarter = ""
    Patreon = ""
    Steam = ""
    Twitch = ""
    Strava = ""
    Skype = ""
    Whatsapp = ""
    Zhihu = ""
    Douban = ""
    Angellist = ""
    Slidershare = ""
    Jsfiddle = ""
    Deviantart = ""
    Behance = ""
    Dribbble = ""
    Wordpress = ""
    Vine = ""
    Googlescholar = ""
    Researchgate = ""
    Mastodon = ""
    Thingiverse = ""
    Devto = ""
    Gitea = ""
    XMPP = ""
    Matrix = ""
    Bilibili = ""
    Email = "xxxx@xxxx.com"
    RSS = true # 

  #  文章页面配置
  [params.page]
    #  是否在主页隐藏一篇文章
    hiddenFromHomePage = false
    #  是否在搜索结果中隐藏一篇文章
    hiddenFromSearch = false
    #  是否使用 twemoji
    twemoji = false
    # 是否使用 lightgallery
    lightgallery = false
    #  是否使用 ruby 扩展语法
    ruby = true
    #  是否使用 fraction 扩展语法
    fraction = true
    #  是否使用 fontawesome 扩展语法
    fontawesome = true
    # 是否在文章页面显示原始 Markdown 文档链接
    linkToMarkdown = true
    #  是否在 RSS 中显示全文内容
    rssFullText = false
    #  目录配置
    [params.page.toc]
      # 是否使用目录
      enable = true
      #  是否保持使用文章前面的静态目录 #修改为动态
      keepStatic = false
      # 是否使侧边目录自动折叠展开
      auto = true
    #  代码配置
    [params.page.code]
      # 是否显示代码块的复制按钮
      copy = true
      # 默认展开显示的代码行数
      maxShownLines = 10
    #  KaTeX 数学公式
    [params.page.math]
      enable = true
      # 默认块定界符是 $$ ... $$ 和 \\[ ... \\]
      blockLeftDelimiter = ""
      blockRightDelimiter = ""
      # 默认行内定界符是 $ ... $ 和 \\( ... \\)
      inlineLeftDelimiter = ""
      inlineRightDelimiter = ""
      # KaTeX 插件 copy_tex
      copyTex = true
      # KaTeX 插件 mhchem
      mhchem = true
    #  Mapbox GL JS 配置
    [params.page.mapbox]
      # Mapbox GL JS 的 access token
      accessToken = ""
      # 浅色主题的地图样式
      lightStyle = "mapbox://styles/mapbox/light-v9"
      # 深色主题的地图样式
      darkStyle = "mapbox://styles/mapbox/dark-v9"
      # 是否添加 NavigationControl
      navigation = true
      # 是否添加 GeolocateControl
      geolocate = true
      # 是否添加 ScaleControl
      scale = true
      # 是否添加 FullscreenControl
      fullscreen = true
    #  文章页面的分享信息设置
    [params.page.share]
      enable = true
      Twitter = true
      Facebook = true
      Linkedin = false
      Whatsapp = true
      Pinterest = false
      Tumblr = false
      HackerNews = false
      Reddit = false
      VK = false
      Buffer = false
      Xing = false
      Line = true
      Instapaper = false
      Pocket = false
      Digg = false
      Stumbleupon = false
      Flipboard = false
      Weibo = true
      Renren = false
      Myspace = true
      Blogger = true
      Baidu = false
      Odnoklassniki = false
      Evernote = true
      Skype = false
      Trello = false
      Mix = false
 
    #  第三方库配置
    [params.page.library]
      [params.page.library.css]
        # someCSS = "some.css"
        # 位于 "assets/"
        # 或者
        # someCSS = "https://cdn.example.com/some.css"
      [params.page.library.js]
        # someJavascript = "some.js"
        # 位于 "assets/"
        # 或者
        # someJavascript = "https://cdn.example.com/some.js"
    #  页面 SEO 配置
    [params.page.seo]
      # 图片 URL
      images = []
      # 出版者信息
      [params.page.seo.publisher]
        name = ""
        logoUrl = ""

  #  TypeIt 配置
  [params.typeit]
    # 每一步的打字速度 (单位是毫秒)
    speed = 100
    # 光标的闪烁速度 (单位是毫秒)
    cursorSpeed = 1000
    # 光标的字符 (支持 HTML 格式)
    cursorChar = "|"
    # 打字结束之后光标的持续时间 (单位是毫秒, "-1" 代表无限大)
    duration = -1

  # 网站验证代码，用于 Google/Bing/Yandex/Pinterest/Baidu
  [params.verification]
    google = ""
    bing = ""
    yandex = ""
    pinterest = ""
    baidu = ""

  #  网站 SEO 配置
  [params.seo]
    # 图片 URL
    image = ""
    # 缩略图 URL
    thumbnailUrl = ""

  #  网站分析配置
  [params.analytics]
    enable = false
    # Google Analytics
    [params.analytics.google]
      id = ""
      # 是否匿名化用户 IP
      anonymizeIP = true
    # Fathom Analytics
    [params.analytics.fathom]
      id = ""
      # 自行托管追踪器时的主机路径
      server = ""

  #  Cookie 许可配置
  [params.cookieconsent]
    enable = true
    # 用于 Cookie 许可横幅的文本字符串
    [params.cookieconsent.content]
      message = ""
      dismiss = ""
      link = ""

  #  第三方库文件的 CDN 设置
  [params.cdn]
    # CDN 数据文件名称, 默认不启用
    # ("jsdelivr.yml")
    # 位于 "themes/LoveIt/assets/data/cdn/" 目录
    # 可以在你的项目下相同路径存放你自己的数据文件:
    # "assets/data/cdn/"
    data = ""

  #  兼容性设置
  [params.compatibility]
    # 是否使用 Polyfill.io 来兼容旧式浏览器
    polyfill = false
    # 是否使用 object-fit-images 来兼容旧式浏览器
    objectFit = false

# Hugo 解析文档的配置
[markup]
  # 语法高亮设置
  [markup.highlight]
    codeFences = true
    guessSyntax = true
    lineNos = true
    lineNumbersInTable = true
    # false 是必要的设置
    # (https://github.com/dillonzq/LoveIt/issues/158)
    noClasses = false
  # Goldmark 是 Hugo 0.60 以来的默认 Markdown 解析库
  [markup.goldmark]
    [markup.goldmark.extensions]
      definitionList = true
      footnote = true
      linkify = true
      strikethrough = true
      table = true
      taskList = true
      typographer = true
    [markup.goldmark.renderer]
      # 是否在文档中直接使用 HTML 标签
      unsafe = true
  # 目录设置
  [markup.tableOfContents]
    startLevel = 2
    endLevel = 6

# 作者配置
[author]
  name = "Isaray"
  email = ""
  link = ""

# 网站地图配置
[sitemap]
  changefreq = "weekly"
  filename = "sitemap.xml"
  priority = 0.5

# Permalinks 配置
[Permalinks]
  # posts = ":year/:month/:filename"
  posts = ":filename"

# 隐私信息配置
[privacy]
  #  Google Analytics 相关隐私 (被 params.analytics.google 替代)
  [privacy.googleAnalytics]
    # ...
  [privacy.twitter]
    enableDNT = true
  [privacy.youtube]
    privacyEnhanced = true

# 用于输出 Markdown 格式文档的设置
[mediaTypes]
  [mediaTypes."text/plain"]
    suffixes = ["md"]

# 用于输出 Markdown 格式文档的设置
[outputFormats.MarkDown]
  mediaType = "text/plain"
  isPlainText = true
  isHTML = false

# 用于 Hugo 输出文档的设置
[outputs]
  # 
  home = ["HTML", "RSS", "JSON"]
  page = ["HTML", "MarkDown"]
  section = ["HTML", "RSS"]
  taxonomy = ["HTML", "RSS"]
  taxonomyTerm = ["HTML"]

```

