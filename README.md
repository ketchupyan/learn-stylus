### 我为什么选择stylus
因为stylus比sass更加优秀，sass是基于ruby，而ruby对中文支持不友好，服务器也在美国，经常被墙，相反stylus 基于node.js npm包，  安装和使用都超级方便，总而言之，我熟悉nodejs不熟悉ruby，nodejs很方便，所以stylus使用也会很方便。

### 那么stylus到底是什么呢
stylus其本质上做的事情与sass/less一样是以近似脚本程序的方式书写CSS代码，但是方便程度：stylus>sass>less.
给个栗子：
<pre>
$bg_color = #f5f5f5
$base_font = 'Open Sans', sans-serif
*
    margin 0
    padding 0
html, body
    min-height 100%
    height 100%
body
    background $bg_color
    font-family $base_font
    font-size 14px
</pre>
是不是很奇怪，什么分号，逗号，冒号都没了，甚至还多了$这个奇怪的东西，但是他得出的css效果是这样的
<pre>
* {
  margin: 0;
  padding: 0;
}
html,body {
  min-height: 100%;
  height: 100%;
}
body {
  background: #f5f5f5;
  font-family: 'Open Sans', sans-serif;
  font-size: 14px;
}
</pre>
哇，我滴个乖乖，这么神奇的吗
对的，就是这么神奇，那么我们来看一下使用stylus需要准备什么，我用一个魅族的锁屏界面来进行一步一步教学。

### 需要准备什么
1. 要电脑的<br/>
电脑还是有的就不po出来了
2. 然后准备一个learn-stylus的文件夹<br/>
准备一个learn-stylus的文件夹，并在其中准好lock.html和lock.styl的文件
3. 要安装好nodejs的<br/>
<pre>
$ npm install stylus
npm WARN saveError ENOENT: no such file or directory, open '/Users/dddnkj/Desktop/workspace/learn-stylus/package.json'
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN enoent ENOENT: no such file or directory, open '/Users/dddnkj/Desktop/workspace/learn-stylus/package.json'
npm WARN learn-stylus No description
npm WARN learn-stylus No repository field.
npm WARN learn-stylus No README data
npm WARN learn-stylus No license field.

+ stylus@0.54.5
added 20 packages in 27.45s
</pre>
神奇的产生了下面的效果,会多出两个文件<br/>
4. 生成css文件<br/>
<pre>
stylus lock.styl -o lock.css
compiled lock.css
</pre>
你的文件夹又会多一个lock.css的文件<br/>
准备完成，接下来就是撸代码了。

###撸代码
* lock.html
``` 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="http://g.tbcdn.cn/mtb/lib-flexible/0.3.4/??flexible_css.js,flexible.js"></script>
    <title>LOCk</title>
     <link rel="stylesheet" href="/lock.css" type="text/css">
</head>
<body>
<div class="page">
    <div class="page_hd">输入密码</div>
    <div class="page_content">
       <div class="page_content__number">
       <div class="numberleft">
           <div class="number">1</div>
           <div class="number">4</div>
           <div class="number">7</div>
       </div>
        <div class="numbermid">
           <div class="number">2</div>
           <div class="number">5</div>
           <div class="number">8</div>
       </div>
        <div class="numberright">
           <div class="number">3</div>
           <div class="number">6</div>
           <div class="number">9</div>
       </div>
       </div>
       <div class="zero number">0</div>
    </div>
    <div class="page_foot"></div>
    <span class="page_foot__left">紧急呼叫</span>
    <span class="page_foot__right">清除</span>
    </div>
</div>
</body>
</html>

``` 
* lock.styl
``` 
$background_image = 'https://images.unsplash.com/photo-1440613905118-99b921706b5c?ixlib=rb-0.3.5&q=80&fm=jpg&crop=entropy&w=1080&fit=max&s=255b304482a2f50d0917f3de7b06251e'
*
    margin 0 auto
    padding 0 auto
    
.page
    position absolute
    width 100%
    height 100%
    background-image url($background_image)
    background-repeat no-repeat
.page, .page_hd
    width 1.851851rem
    height 0.555555rem
    margin 2.962962rem auto
    color #fff
    font-size 0.462962rem
.number 
    width 1.629629rem;
    height 1.629629rem;
    margin-bottom 0.722222rem
    font-size 25px
    font-weight 100
    text-align center
    line-height 1.629629rem
    color #e8ffff
    border 2px solid #81969c
    border-radius 50%
.page_content 
    position relative
    margin-top 2.592592rem
.page_content__number 
    display flex
    width 6.962962rem
    height 6.333333rem
    margin-left 1.458518rem
    font-size 400
.numberleft 
    margin-right 1.037037rem
    
.numbermid 
    margin-right: 1.037037rem
.zero 
    margin-top 0.722222rem
    margin-left 4.185185rem
.page_foot 
    position relative
    width 100%
    height 0.592592rem
    margin-bottom 0.259259rem
        
.page_foot__left 
    color rgba(255,255,255,0.5)
    font-size .444444rem
    display inline-block
    margin-left 0.185185rem
    margin-right 6.881851rem
.page_foot__right 
    color rgba(255,255,255,0.5)
    font-size 0.444444rem
* lock.styl
``` 
在终端执行命令stylus lock.styl -o lock.css会得到lock.css文件
```
* {
  margin: 0 auto;
  padding: 0 auto;
}
.page {
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: url("https://images.unsplash.com/photo-1440613905118-99b921706b5c?ixlib=rb-0.3.5&q=80&fm=jpg&crop=entropy&w=1080&fit=max&s=255b304482a2f50d0917f3de7b06251e");
  background-repeat: no-repeat;
}
.page,
.page_hd {
  width: 1.851851rem;
  height: 0.555555rem;
  margin: 2.962962rem auto;
  color: #fff;
  font-size: 0.462962rem;
}
.number {
  width: 1.629629rem;
  height: 1.629629rem;
  margin-bottom: 0.722222rem;
  font-size: 25px;
  font-weight: 100;
  text-align: center;
  line-height: 1.629629rem;
  color: #e8ffff;
  border: 2px solid #81969c;
  border-radius: 50%;
}
.page_content {
  position: relative;
  margin-top: 2.592592rem;
}
.page_content__number {
  display: flex;
  width: 6.962962rem;
  height: 6.333333rem;
  margin-left: 1.458518rem;
  font-size: 400;
}
.numberleft {
  margin-right: 1.037037rem;
}
.numbermid {
  margin-right: 1.037037rem;
}
.zero {
  margin-top: 0.722222rem;
  margin-left: 4.185185rem;
}
.page_foot {
  position: relative;
  width: 100%;
  height: 0.592592rem;
  margin-bottom: 0.259259rem;
}
.page_foot__left {
  color: rgba(255,255,255,0.5);
  font-size: 0.444444rem;
  display: inline-block;
  margin-left: 0.185185rem;
  margin-right: 6.881851rem;
}
.page_foot__right {
  color: rgba(255,255,255,0.5);
  font-size: 0.444444rem;
}
```
大功告成，得到效果图如下

### 最后说一下stylus的好处
1. 复用性高，这是每一个份代码需要的
2. 更好修改
3. 节省三分之一的时间

