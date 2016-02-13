<!DOCTYPE.md>
.md xmlns="http://www.w3.org/1999/...md" xml:lang="zh-CN">
<head>
<meta http-equiv="Content-Type" content="text.md; charset=utf-8" />
<meta name="generator" content="Python script by program.think@gmail.com" />
<meta name="provider" content="program-think.blogspot.com" />
<link type="text/css" rel="stylesheet" href="../../css/program-think.css" />
<title>如何用GreaseMonkey扩展Google Reader - 编程随想的博客</title>
</head>
<body>
<div id="main" style="width:100%;">
<h1><a href="../../index.md" title="回到首页">如何用GreaseMonkey扩展Google Reader</a></h1>
<div class="post-info"><span class="date-header">2011-11-02</span><a href="../../tags/IT.E8BDAFE4BBB6E4BB8BE7BB8D.md" class="tag">IT.软件介绍</a> <a href="../../tags/IT.md" class="tag">IT</a> </div>
<hr>
<div class="post">
&#12288;&#12288;在说正题之前先插一句：Google 为了强行推广 G+，把 Google 阅读器的社交功能都阉了。今后，大伙儿如果想看俺的分享，除了继续用 Google Reader 订阅俺的博客（俺博客的RSS订阅地址： <a href="http://feeds2.feedburner.com/programthink" target="_blank">http://feeds2.feedburner.com/programthink</a> ），还可以在 Google+ 圈养（俺的 G+ 页面： <a href="https://plus.google.com/113559088971921339544/" target="_blank">https://plus.google.com/113559088971921339544/</a> ）。<br /><br /><h2>★引子</h2><br />&#12288;&#12288;话说俺一直是 Google Reader 的重度使用者——从2005年10月至今，俺的阅读数已超过13万。上周 Google 放出风声说要改版，俺还是满心期待的。谁曾想，昨天（11年11月1日）发布的新版本，那界面真是让人大跌眼镜——怎一个"烂"字了得！<br />不过，抱怨归抱怨，眼下暂时还没有合适的替代品，Google 阅读器还得接着用下去。为了不至于天天面对这么一个恶心的界面，俺发扬"自己动手丰衣足食"的DIY精神，亲自操刀修改阅读器的界面。有兴趣的同学，可以看看俺的经验分享。<!--program-think--><br /><br /><h2>★为啥要美化阅读器？</h2><br />&#12288;&#12288;对于老用户而言，新版的界面简直是惨不忍睹——到处都是多余的空白，显得非常不紧凑。比如：文章的列表界面，间距也太大了。现在一屏能显示的帖子数只有原来的一半。这样一来，大大降低了阅读的效率，浪费的大伙儿的时间。<br />估计很多网友逆来顺受惯了。不管网站推出多么烂的界面，他们都默默忍受。但是，在当今 Web 盛行的互联网时代，普通用户是完全可以自己操刀修改网站界面滴（而且<b>几乎不需要专业技术</b>）！此中之奥妙，在于<b>GreaseMonkey</b>这一大杀器。<br /><br /><h2>★GreaseMonkey 扫盲</h2><br /><h3>◇GreaseMonkey 是啥玩意儿？</h3><br />&#12288;&#12288;GreaseMonkey 俗称"油猴"<img src="../../images/2011/11/-trXAUb61lyW1COfDwja_R0ZiTcZorz62AlBTXFiNYSPh18N1fk8w1pzBhQ2kD65Ae3jL1lYDM-cK3iPu1jJdDiVucQgT7ymFeNN4AMvAZ6XcwlmkyocZ0zfRrMaYmldJNg" width="64">，官网在"<a href="http://www.greasespot.net/" target="_blank" rel="nofollow">这里</a>"，维基百科的介绍在"<a href="http://zh.wikipedia.org/zh-cn/Greasemonkey" target="_blank" rel="nofollow">这里</a>"。它早先是 Firefox 的一款插件。但它可不是普通的插件，<b>它是插件的插件</b>。简单来说，你可以通过 JavaScript 脚本（以下简称 "JS脚本"），来扩展它的功能。因此，只要JS脚本能搞定的事情，它都能搞定。而且，你可以指定某个脚本仅仅作用在某个URL（某个网站）——也就是把脚本跟网站绑定。这样一来，就可以专门针对某个网站的页面进行调整。<br /><br /><h3>◇油猴能干啥？</h3><br />&#12288;&#12288;看到这里，肯定有人要问了，这些油猴脚本，都能干些啥事捏？俺举几个例子：<br />比如，某个网站的广告条太碍眼，你可以用JS脚本把广告条干掉。<br />比如，你喜欢到某个视频网站去看视频，但是这个视频网站没有下载按钮。于是你就可以用JS脚本给每个视频加上一个下载按钮，方便你下载到本地收藏。<br /><br /><h3>◇不会写JS脚本，咋办？</h3><br />&#12288;&#12288;很多同学会担心，自己不懂得写JS脚本。其实大可不必害怕。因为油猴已经非常的普及，你能想到的大部分需求，早都已经有人（多半是老外）写好了，而且分享出来了。<br />&#12288;&#12288;在此，向列位看官隆重介绍：全球最大的（没有之一）油猴脚本收集站点——<a href="http://userscripts.org/" target="_blank" rel="nofollow">UserScripts.org</a>。这上面的脚本数量，已经到了6位数。由于脚本太多，你第一次上去的时候，建议先看<a href="http://userscripts.org/tags" target="_blank" rel="nofollow">它的标签分类</a>。根据分类，就可以比较容易滴找到自己要的脚本。<br /><br /><h3>◇支持哪些浏览器？</h3><br />&#12288;&#12288;前面说了，油猴早先是 Firefox 插件，自然是天生支持火狐。后来 Google 看到这玩意儿挺普及，就让 Chome 浏览器原生支持油猴脚本。也就是说，你无需安装额外插件，就可以让 Chrome 运行油猴脚本。Opera从 8.0 开始，貌似也兼容了油猴脚本（俺没试过，不知兼容性如何）。至于使用 IE 的同学，暂时无福享用了（建议尽早抛弃 IE 这种老土的浏览器）。<br /><br /><h2>★增强阅读器功能的脚本</h2><br />&#12288;&#12288;既然刚才提到了 UserScripts 网站，随便推荐几个脚本，可以为阅读器增加额外的功能。如果你常用 Google 阅读器，可以去尝试一下。<br /><br /><h3>◇<a href="http://userscripts.org/scripts/show/9455" target="_blank" rel="nofollow">Google Reader Preview Enhanced</a></h3><br />&#12288;&#12288;这个脚本是专门对付那些没有全文输出的RSS（不输出全文的博客，非常讨厌）。当你碰到某个只输出摘要的博文，只要按一下快捷键（Shift+V），该脚本就会在阅读器的正文窗口里，自动显示该博文的全部正文。有了它，你无需离开 Google Reader 就可以看只输出摘要的博客了。<br /><br /><h3>◇<a href="http://userscripts.org/scripts/show/8782" target="_blank" rel="nofollow">Google Reader - Colorful List View</a></h3><br />&#12288;&#12288;此脚本会给文章列表中的每一个帖子着色。相同订阅源文章，会标注相同的颜色。当你选中某个文件夹（Folder） 时，就可以很清楚看出那些文章来自同一个订阅源。<br />&#12288;&#12288;补充一下：貌似这次改版后，此插件不灵了，也不晓得插件的作者啥时候出新版本。<br /><br /><h3>◇<a href="http://userscripts.org/scripts/show/23671" target="_blank" rel="nofollow">Google Reader Filter</a></h3><br />&#12288;&#12288;看名称就知道，此脚本提供针对文章的过滤功能。你可以设置一些过滤规则，来决定哪些文章在列表中高亮显示，那些文章被排除（变灰）。另外，它还可以帮你隐藏重复的文章。<br /><br /><h3>◇<a href="http://userscripts.org/scripts/show/21909" target="_blank" rel="nofollow">Google Reader Subscribers Count</a></h3><br />这个脚本会在窗口的右下角显示当前RSS的订阅者数量。<br /><br /><h2>★优化阅读器界面的脚本</h2><br />&#12288;&#12288;除了上述这些增强功能的脚本，还有很多脚本是用来美化 Google Reader 界面的。这些脚本中，有些是历史悠久的，有些是昨天才发布的（专门针对改版后的丑陋界面）。顺便说一下，Google Reader 刚改版，就冒出一堆美化界面的脚本，可见这次改版非常不得人心。<br /><br /><h3>◇<a href="http://userscripts.org/scripts/show/6415" target="_blank" rel="nofollow">Google Reader for wider screens</a></h3><br />&#12288;&#12288;这个脚本有些年头了，而且很小巧。它可以充分利用屏幕的空间来显示文章正文，如果是宽屏显示器，则效果更佳。以下是俺截的两张对比图：<br /><br />调整前的正文布局<br /><center><img src="../../images/2011/11/N2hkIs3by-5b6mqcN2ITii6S9SE96nKq12dtTK8EBYXaGcq-YvecGstM8mlRRLGGf8adUFW0vm-jUo_gUdTHXBIPKLmyvL2yHHpRTYio3ayfWggUC9xvkPDTDlS_zP0qYC4" alt="不见图 请翻墙" width="75%"></center><br />调整后的正文布局<br /><center><img src="../../images/2011/11/8Zty3iECbcIYQPC2cCKQy4tmpJzvE2vlLGcVVpPS-7TOJGFbGhK4MQ7PeIkGj69k5qPx1k7RUFA-TrX1r5Ez7Pib68cvogIfzE2oISiilSS0PF8uqYxJqqfUtt6JjxwYoNk" alt="不见图 请翻墙" width="75%"></center><br /><h3>◇<a href="http://userscripts.org/scripts/show/58577" target="_blank" rel="nofollow">Google Reader Absolutely Customizable</a></h3><br />&#12288;&#12288;这个脚本有一大坨代码，但是功能也挺多。它在阅读器的界面里，加入了一个定制菜单。通过此菜单，你可以凭自己的喜好，对很多界面元素进行调整或显示/隐藏。<br />以下是脚本作者提供的效果图：<br /><br />定制菜单<br /><center><img src="../../images/2011/11/xrTR6vj599ClayJsTGN2AVhcsWnIU1S9-44NdL0pY6anWNJ0mBwgDb3sCnVWQ8x0OVyNitAkdiJxjzStMIqGsuggKVEO9FnUZQCeZvA1w6BzoXAGuY9k6--Uh176vesAxJy1" alt="不见图 请翻墙"></center><br />选项对话框<br /><center><img src="../../images/2011/11/dSOlQFlzRBIzjewg8vi2lr1FmRWBJcjHtaE9YDpxn1HTYmJFuJr1XzRjSDwV_cPAJWhO3DnGT47aAomiZKxtR6GsIMP3iy3PKhVWrea9jb0dZdbRhpnqfsHEyQ8nj9YwiM1E" alt="不见图 请翻墙"></center><br /><h3>◇<a href="http://userscripts.org/scripts/show/116850" target="_blank" rel="nofollow">Google Reader Demarginfier</a></h3><br />&#12288;&#12288;这是改版当天就推出的脚本，专门针对改版后的土B界面（此作者动手真快啊）。它可以压缩阅读器搜索条和工具条的高度、压缩文章列表的行高、压缩左边导航树的左边距。<br /><br /><h3>◇<a href="http://userscripts.org/scripts/show/116888" target="_blank" rel="nofollow">Google Reader - Compact Design</a></h3><br />&#12288;&#12288;又一个改版当天快速推出的脚本，功能跟前一个类似。同样能压缩阅读器搜索条和工具条的高度、压缩文章列表的行高、还能压缩左边导航书每个条目的行高（这个功能上面的脚本没有），但是缺少压缩左边导航树的左边距的功能。<br />以下是脚本作者提供的效果图：<br /><center><img src="../../images/2011/11/_lkg0zFy8Tz01UMwIa7YTXMf-hPnInJ5IJ7po0njhFWmfoqEKdJhZ_doG5vG4FgwCyinpOx1IYobq5m0HqWolGB1WhJV42UvCX0u07VO5OvLVDfB2Fn0XqdO06JuKZPIWVGZ" alt="不见图 请翻墙" width="75%"></center><br /><h3>◇<a href="../../images/2011/11/_lkg0zFy8Tz01UMwIa7YTXMf-hPnInJ5IJ7po0njhFWmfoqEKdJhZ_doG5vG4FgwCyinpOx1IYobq5m0HqWolGB1WhJV42UvCX0u07VO5OvLVDfB2Fn0XqdO06JuKZPIWVGZ" target="_blank" rel="nofollow">GRSeven for Greasemonkey</a></h3><br />&#12288;&#12288;这可是咱天朝国产的脚本，也是专门针对改版后的土B界面。它的特色是：把界面顶部的搜索条和工具条合并掉，避免上方空间的浪费。<br />以下是脚本作者提供的效果图：<br /><center><img src="../../images/2011/11/pN7KiqF4ukW2GanaqffKp5CCAzX_xHYUUeCzigtx62Ug2Nl91ttTzYOCgbjf21McmcJ3YkNa3h21y5HjWmeSYx_kPSqmUjCAAZfYR0_tLK_plgWvkQINNoADU0MUGo1xNpcE" alt="不见图 请翻墙" width="75%"></center><br /><h2>★自己动手美化阅读器</h2><br />&#12288;&#12288;请注意，本章节是留给那些富有 DIY 精神，并且略懂网页基础知识的网友。假如你对上述这些界面优化脚本都不满意，想自己动手写一个脚本来美化阅读器。那么，本章节对你应该有帮助。<br />&#12288;&#12288;反之，如果你对技术一窍不通，或者怕麻烦、或者没时间，请略过本章节。<br /><br /><h3>◇如何美化？</h3><br />&#12288;&#12288;上述这些脚本对 Google Reader 的界面调整，说白了都是修改CSS（层叠样式表）。在油猴脚本中，可以调用 <b>GM_addStyle</b> 函数，往当前页面加入一个新的样式表。如果你略懂 CSS，搞清楚这些脚本的代码应该对你来说就易如反掌。<br /><br /><h3>◇调整正文宽度</h3><br />&#12288;&#12288;以下代码用于修改正文的显示宽度，让正文的宽度能充满屏幕。<br /><blockquote style="background-color:#DDD;"><font face="Courier New">GM_addStyle(".entry .entry-body, .entry .entry-title { max-width:100% !important; }");</font><br /></blockquote><br /><h3>◇压缩搜索条高度</h3><br />&#12288;&#12288;以下代码调整阅读器搜索条的高度（也就是阅读器上方有：Logo、搜索框、搜索按钮的那一行）。代码中的 40px 和 6px 表示高度（像素为单位），你可以根据自己喜好，微调这2个数字。<br /><blockquote style="background-color:#DDD;"><font face="Courier New">GM_addStyle("#top-bar { height:<b>40px</b> !important; }");<br />GM_addStyle("#search { padding:<b>6px</b> 0px !important; }");</font><br /></blockquote><br /><h3>◇压缩工具条高度</h3><br />&#12288;&#12288;以下代码调整工具条的高度（也就是阅读器上方有："订阅"、"标为已读"、"供稿设置"等按钮的那一行）。<br /><blockquote style="background-color:#DDD;"><font face="Courier New">GM_addStyle("#viewer-header { height:<b>40px</b> !important; }");<br />GM_addStyle("#lhn-add-subscription-section { height:<b>40px</b> !important; }");<br />GM_addStyle("#lhn-add-subscription, #viewer-top-controls-container { margin-top:-15px !important; }");</font><br /></blockquote><br /><h3>◇压缩文章列表的行高</h3><br />&#12288;&#12288;新版界面的文章列表，行高大得离谱了，必须得调小。如下代码可以搞定。<br /><blockquote style="background-color:#DDD;"><font face="Courier New">GM_addStyle("#entries { padding:0px !important; }");<br />// 1.2em 表示行高是字体高度的1.2倍。<br />GM_addStyle(".collapsed { line-height:<b>1.2em</b> !important; padding:2px 0 !important; }");<br />// 设置列表左边星号的位置<br />GM_addStyle(".entry-icons { top:<b>12px</b> !important }");<br />// 设置列表里文字标题的位置<br />GM_addStyle(".entry-source-title { top:<b>2px</b> !important }");<br />GM_addStyle(".entry-secondary { top:<b>2px</b> !important }");<br />// 设置列表右边"打开原始URL"图标的位置<br />GM_addStyle(".entry-main .entry-original { top:<b>12px</b> !important }");</font><br /></blockquote><br /><h3>◇压缩导航树的左边距</h3><br />&#12288;&#12288;导航树左边留了一大块空白，也不知要作甚？用如下代码压缩掉。<br /><blockquote style="background-color:#DDD;"><font face="Courier New">GM_addStyle(".section-minimize { left:0px !important }");<br />GM_addStyle("#overview-selector, #lhn-selectors .selector, .folder .name.name-d-0, #sub-tree-header { padding-left:15px !important; }");<br />GM_addStyle(".folder .folder .folder-toggle { margin-left:12px !important }");<br />GM_addStyle(".folder .sub-icon, .folder .folder&gt;a&gt;.icon { margin-left:27px !important }");<br />GM_addStyle(".folder .folder&gt;ul .icon { margin-left:34px !important }");<br />GM_addStyle(".folder .folder .name-text { max-width:160px; !important }");<br />GM_addStyle("#reading-list-selector .label { display:inline !important }");</font><br /></blockquote><br /><h3>◇压缩导航树不同部分之间的间隙</h3><br />&#12288;&#12288;导航树由4部分组成，分别是："主页"(Home)、"所有条目"(All items)、"探索"(Explore)、"订阅"(Subscriptions)。这4块之间的间隙太大，用如下代码压缩。<br /><blockquote style="background-color:#DDD;"><font face="Courier New">GM_addStyle(".selectors-footer { margin-bottom:0px !important; padding-bottom:0px !important; }");<br />GM_addStyle(".lhn-section-footer { margin-bottom:0px !important; padding-bottom:0px !important; }");</font><br /></blockquote><br /><h3>◇隐藏导航树的某些部分</h3><br />&#12288;&#12288;导航树的这4部分，通常是"订阅"用得最多。其它3部分如果用得少，嫌它们太占空间，可以用如下代码隐掉。<br /><blockquote style="background-color:#DDD;"><font face="Courier New">// 隐藏"主页"<br />GM_addStyle("#overview-selector { display:none !important; }");<br />// 隐藏"所有条目"<br />GM_addStyle("#lhn-selectors { display:none !important; }");<br />// 隐藏"探索"<br />GM_addStyle("#lhn-recommendations { display:none !important; }");</font><br /></blockquote><br /><h3>◇调整导航树的宽度</h3><br />&#12288;&#12288;由于不同人的偏好及屏幕尺寸各有差异。因此，很多刁钻滴用户（比如俺）对导航树占的宽度不满意。你可以用如下代码来调整。代码中的 240px 表示宽度，你可以根据喜好来调整。在这3行代码中，此数值要保持一致。<br /><blockquote style="background-color:#DDD;"><font face="Courier New">GM_addStyle("#nav, #nav * { max-width:<b>240px</b> !important; }");<br />GM_addStyle("#nav { width:<b>240px</b> !important; }");<br />GM_addStyle("#chrome { margin-left:<b>240px</b> !important; }");</font><br /></blockquote><br /><h2>★结尾</h2><br />&#12288;&#12288;今天说了这一大坨，也不知大伙儿有兴趣不？如果大伙儿对油猴的兴趣比较大，俺可以找时间再介绍其它一些实用的脚本。<div class="blogger-post-footer">
</div>
<hr>
<div class="copyright">
<h4>版权声明</h4>
本博客所有的原创文章，作者皆保留版权。转载必须包含本声明，保持本文完整，并以超链接形式注明作者<a href="mailto:program.think@gmail.com">编程随想</a>和本文原始网址：<br>
<a href="2011/11/greasemonkey-scripts-for-google-reader.md">2011/11/greasemonkey-scripts-for-google-reader.md</a>
</div>
</div>
</body>
<.md>