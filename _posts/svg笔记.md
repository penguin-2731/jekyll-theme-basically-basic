# 第一篇
---
layout: page                               
title:震惊，2021年了竟然还有人不知道svg

date: 2021-01-06

---
### svg的定义
SVG是XML语言的一种形式，有点类似XHTML，它可以用来绘制矢量图形。它可以成为任何复杂的组合图形。SVG支持渐变、旋转、滤镜效果、JavaScript接口等等功能。

各种SVG浏览器是有差异的，因此很可能你制作了一个SVG图形，并且用一个工具调试正常后，却在另外一个浏览器中无法正常显示。这是因为不同的浏览器支持SVG标准的程度不同。

---
layout: page                             

title: Superman不止超人会飞！这个单词同样神奇！     
date: 2021-01-06                               

categories:
- SVG制作

tags:
 - svg

---
我不相信你不好奇！
<!--more-->
## SVG的文本移动
下面是superman这个单词沿着一条带拐弯的路径移动。

<svg width="640" height="480" version="1.1">
<g transform="translate(150,150)">
<path d="M0,0 L70,70 L150,270 L-230,-470" style="fill:restart;stroke:red;stroke-width:2"/>
<text x="0" y="0" font-size="37" visibility="hidden"
stroke="red" stroke-width="2">
Superman
<set attributeName="visibility"
attributeType="CSS" to="visible"
begin="1s" dur="5s" fill="freeze"/>
<animateMotion path="M0,0 L70,70 L150,270 L-230,-470"
begin="0.5s" dur="10s" fill="restart" rotate="auto"/>
</text>
</g>
</svg>

- 这个例子是老师在课堂上展示过给我们看的，课后我回去将其修改成上面所示那样。
- 我们先使用了<set>元素，使得superman能够显示出来，并且沿着路径移动。时间设置为5s和10s。设置"rotate"属性为"auto"，使Superman到了拐弯的地方时继续紧贴着路径前进，而不是维持原来的方向："fill"属性设置为"restart"，表示动画播放完毕后，就恢复原来的画面状态。
- path是路径的数据，通过空格和逗号进行路径数据的改变改变文字的走向。
> 代码可供尝试，删除了部分导致显示不完全的代码:
1. <svg width="640" height="480" version="1.1"
2. g transform="translate(150,150)">
3. path d="M0,0 L70,70 L150,270 L-230,-470" style="fill:restart;stroke:red;stroke-width:2"/>
4. <text x="0" y="0" font-size="37" visibility="hidden"
5. stroke="red" stroke-width="2">
6. Superman
7. <set attributeName="visibility"
8. attributeType="CSS" to="visible"
9. begin="1s" dur="5s" fill="freeze"/>
10. <animateMotion path="M0,0 L70,70 L150,270 L-230,-470"
11. begin="0.5s" dur="10s" fill="restart" 
# 第二篇
---
layout: page                               
title: 螺旋丸、写轮眼熟悉吗？我用SVG旋转做了一个“万花筒写轮眼”！                          
excerpt_separator: "<!--more-->"            
date: 2021-01-06   

categories:
- SVG制作

tags:
 - svg


---

<!--more-->
## SVG的旋转动画

<head>
		<meta charset="utf-8" />
	</head>
<svg aria-hidden="true" focusable="false" data-prefix="fas" data-icon="atom" class="svg" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><path fill="currentColor" d="M413.03 256c40.13-54.89 41.51-98.62 25.14-128-10.91-19.52-40.54-50.73-116.33-41.88C300.36 34.89 267.64 0 224 0s-76.36 34.89-97.84 86.12C50.43 77.34 20.73 108.48 9.83 128c-16.38 29.4-15 73.09 25.14 128-40.13 54.89-41.51 98.62-25.14 128 29.21 52.34 101.68 43.58 116.33 41.88C147.63 477.1 180.36 512 224 512s76.37-34.9 97.84-86.12c14.64 1.7 87.11 10.46 116.33-41.88 16.38-29.4 15-73.09-25.14-128zM63.38 352c-4.03-7.21-.19-24.8 14.95-48.29 6.96 6.53 14.2 12.89 21.87 19.18 1.71 13.71 4 27.08 6.76 40.08-24.56.89-39.89-4.37-43.58-10.97zm36.82-162.88c-7.66 6.29-14.9 12.65-21.87 19.18-15.13-23.5-18.97-41.09-14.95-48.3 3.41-6.14 16.39-11.47 37.92-11.47 1.71 0 3.87.3 5.69.37a472.191 472.191 0 0 0-6.79 40.22zM224 64c9.47 0 22.2 13.52 33.86 37.26-11.19 3.7-22.44 8-33.86 12.86-11.42-4.86-22.67-9.16-33.86-12.86C201.8 77.52 214.53 64 224 64zm0 384c-9.47 0-22.2-13.52-33.86-37.26 11.19-3.7 22.44-8 33.86-12.86 11.42 4.86 22.67 9.16 33.86 12.86C246.2 434.48 233.47 448 224 448zm62.5-157.33c-26.7 19.08-46.14 29.33-62.5 37.48-16.35-8.14-35.8-18.41-62.5-37.48-1.99-27.79-1.99-41.54 0-69.33 26.67-19.05 46.13-29.32 62.5-37.48 16.39 8.17 35.86 18.44 62.5 37.48 1.98 27.78 1.99 41.53 0 69.33zM384.62 352c-3.67 6.62-19 11.82-43.58 10.95 2.76-13 5.05-26.37 6.76-40.06 7.66-6.29 14.9-12.65 21.87-19.18 15.13 23.49 18.97 41.08 14.95 48.29zm-14.95-143.71c-6.96-6.53-14.2-12.89-21.87-19.18a473.535 473.535 0 0 0-6.79-40.22c1.82-.07 3.97-.37 5.69-.37 21.52 0 34.51 5.34 37.92 11.47 4.02 7.22.18 24.81-14.95 48.3zM224 224c-17.67 0-32 14.33-32 32s14.33 32 32 32 32-14.33 32-32-14.33-32-32-32z"></path></svg>
<style>
 .svg
 {
 animation: rotate 5s infinite;
 animation-timing-function:linear;
}
@keyframes rotate{
0% { transform:rotate(0deg);}

100% { transform : rotate(360deg)}
}  
}


</style>

1. 这个例子是首先从font-awesome图标库里面下载好SVG图片素材
2. 然后设置好style的样式，核心样式为animation: rotate 5s infinite，rotate即为旋转的意思
3. 再用@keyframes rotate设置好旋转的角度，包括起始和结束等
4. 再检查一边代码正误即可。
- 设置简单，需要熟悉好旋转的参数。
---
layout: page                             

title: SVG的平移 

date: 2021-01-06                               

categories:
- SVG制作

tags:
 - svg

---
一个简单的平移，是我开始对这个感兴趣的开始！
<!--more-->
---

# 第三篇
## SVG的平移


<svg>
<rect x="50" y="50" width="100" height="50">
<animate attributeType="XML" attributeName="x" 
from="50" to="300" dur="3s" begin="1s"
restart="always" repeatCount="3">
</animate>
</rect>
</svg>

- (attributeType：变化的类型，是HTML还是css)
- 创建一个SVG图形，设定好x，y两个坐标，再设定往哪个轴移动attributeName，再设定from、to既可以设定起始和结束坐标，还有添加过程的时间dur、开始前的时间begin、restart、repeatCount等即可以完成SVG图片的平移动画。
- 你学会了吗？赶紧尝试一下吧！
- 实践才能出真知。
- 我在做这个的时候因为代码忘记加上结束</svg>，导致不断尝试不断查资料，最后仔细检查才修改正确。吸取教训，基础知识要牢记，多动手练习。
---
layout: page
title: SVG有趣的例子
excerpt_separator: "<!--more-->"
date: 2021-01-06

categories:  
- SVG制作

tags:
 - svg

---
SVG+CSS3动画听说很配噢~~

<!--more-->
## SVG有趣的例子
- 颜色会渐变
<head>
  <meta charset="UTF-8">
<style> 
.QXF
{
width:100px;
height:100px;
background:red;
animation:QXF 5s;
animation-iteration-count: infinite;
}

@keyframes QXF
{
from {background:red;}
to {background:blue;}
}



</style>
</head>
<body>

<div class="QXF"></div>
</body>


- 不仅会渐变，还会移动
<head>
  <meta charset="UTF-8">
<style> 
.aaa
{
width:100px;
height:100px;
background:red;
position:relative;
animation:aaa 5s linear 2s infinite alternate;
}

@keyframes aaa
{
0%   {background:red; left:0px; top:0px;}
25%  {background:green; left:200px; top:0px;}
50%  {background:yellow; left:200px; top:200px;}
75%  {background:black; left:0px; top:200px;}
100% {background:red; left:0px; top:0px;}
}
</style>
</head>
<body>
<div class="aaa">动起来</div>

</body>


- 再将SVG和CSS3动画结合起来

<body>
<head>
  <meta charset="UTF-8">
<style> 
.bbb
{
background:red;
position:relative;
animation:bbb 5s linear 2s infinite alternate;
}

@keyframes bbb
{
0%   {background:red; left:0px; top:0px;}
25%  {background:green; left:200px; top:0px;}
50%  {background:yellow; left:200px; top:200px;}
75%  {background:black; left:0px; top:200px;}
100% {background:red; left:0px; top:0px;}
}
</style>
</head>
<svg class="bbb" version="1.1">
  <path d="M150 0 L75 200 L225 200 Z" />
</svg>

</body>

### 除了这种简单的SVG之外，我们可以通过其他网站来获取SVG图
> 例如：font-awesome
- <svg aria-hidden="true" focusable="false" data-prefix="fas" data-icon="heart" class="svg-inline--fa fa-heart fa-w-16" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="currentColor" d="M462.3 62.6C407.5 15.9 326 24.3 275.7 76.2L256 96.5l-19.7-20.3C186.1 24.3 104.5 15.9 49.7 62.6c-62.8 53.6-66.1 149.8-9.9 207.9l193.5 199.8c12.5 12.9 32.8 12.9 45.3 0l193.5-199.8c56.3-58.1 53-154.3-9.8-207.9z"></path></svg>
- <svg aria-hidden="true" focusable="false" data-prefix="fab" data-icon="angellist" class="svg-inline--fa fa-angellist fa-w-14" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><path fill="currentColor" d="M347.1 215.4c11.7-32.6 45.4-126.9 45.4-157.1 0-26.6-15.7-48.9-43.7-48.9-44.6 0-84.6 131.7-97.1 163.1C242 144 196.6 0 156.6 0c-31.1 0-45.7 22.9-45.7 51.7 0 35.3 34.2 126.8 46.6 162-6.3-2.3-13.1-4.3-20-4.3-23.4 0-48.3 29.1-48.3 52.6 0 8.9 4.9 21.4 8 29.7-36.9 10-51.1 34.6-51.1 71.7C46 435.6 114.4 512 210.6 512c118 0 191.4-88.6 191.4-202.9 0-43.1-6.9-82-54.9-93.7zM311.7 108c4-12.3 21.1-64.3 37.1-64.3 8.6 0 10.9 8.9 10.9 16 0 19.1-38.6 124.6-47.1 148l-34-6 33.1-93.7zM142.3 48.3c0-11.9 14.5-45.7 46.3 47.1l34.6 100.3c-15.6-1.3-27.7-3-35.4 1.4-10.9-28.8-45.5-119.7-45.5-148.8zM140 244c29.3 0 67.1 94.6 67.1 107.4 0 5.1-4.9 11.4-10.6 11.4-20.9 0-76.9-76.9-76.9-97.7.1-7.7 12.7-21.1 20.4-21.1zm184.3 186.3c-29.1 32-66.3 48.6-109.7 48.6-59.4 0-106.3-32.6-128.9-88.3-17.1-43.4 3.8-68.3 20.6-68.3 11.4 0 54.3 60.3 54.3 73.1 0 4.9-7.7 8.3-11.7 8.3-16.1 0-22.4-15.5-51.1-51.4-29.7 29.7 20.5 86.9 58.3 86.9 26.1 0 43.1-24.2 38-42 3.7 0 8.3.3 11.7-.6 1.1 27.1 9.1 59.4 41.7 61.7 0-.9 2-7.1 2-7.4 0-17.4-10.6-32.6-10.6-50.3 0-28.3 21.7-55.7 43.7-71.7 8-6 17.7-9.7 27.1-13.1 9.7-3.7 20-8 27.4-15.4-1.1-11.2-5.7-21.1-16.9-21.1-27.7 0-120.6 4-120.6-39.7 0-6.7.1-13.1 17.4-13.1 32.3 0 114.3 8 138.3 29.1 18.1 16.1 24.3 113.2-31 174.7zm-98.6-126c9.7 3.1 19.7 4 29.7 6-7.4 5.4-14 12-20.3 19.1-2.8-8.5-6.2-16.8-9.4-25.1z"></path></svg>
- 获取到SVG图片素材之后，我们就可以发挥自己的创意去进行改造创意了。
