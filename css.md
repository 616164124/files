# css

## 小知识点

工具网站：https://www.learnfk.com/course-css

.点号选中的是class，#选中的是id

各个浏览器是否适配需要添加前缀

1in = 2.54cm = 25.4 mm = 72pt = 6pc = 96px 

可以理解为 1厘米 等于 37.79px

css引入

<link>里面的属性有type、rel、href，其中type固定为text/css，rel（即样式表）固定为stylesheet，href自然指的就是css文件的地址了，语法格式为：

  <link type="text/css" rel="stylesheet"  href="css文件的存放地址">

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=<device-width>, initial-scale=1.0">
    <title>day01</title>
     
  <link rel="stylesheet" type="text/css" href="./styel.css" />
</head>
```



css

```css
/*react中 className="note-abstract"*/
.note-abstract {
    font-size: .75rem;
    color: hsl(60, 4%, 9%);
    opacity: .8;
}
/*<span></span> 标签的样式 */
span {
    margin-left: .3125rem;
    color: #38ba72;
}
```

## day01

1、图片固定

background-color     	    : 背景颜色。
background-image      	  : 背景图片。
background-repeat     	   : 设置背景图像是否及重复。
background-position     	: 设置背景图像的起始位置。
background-attachment   : 背景图像是否固定或者随着页面的其余部分滚动。
background      					: 简写属性，作用是将背景属性设置在一个声明中。

2、字体

- font-family  : 设置字体系列。

- font-style   : 设置字体样式。     **normal**(正常)，斜体(**italic**)和倾斜(**oblique**)

- font-variant : 以小型大写字体或者正常字体显示文本。   *small-caps： 小型的大写字母字体,都是大写的*

- font-weight  : 设置字体的粗细。  可能的值可以是**normal**，**bold**，**bolder**，**lighter**

-  font-size    : 设置字体的大小。可能的值可以是 xx-small，x-small，small，medium，large，x-large，			                                          xx-large，smaller，larger， px size或％。

- font-size-adjust :  简写属性，作用是把所有针对字体的属性设置在一个声明中  值可以是任何数字

  font:italic small-caps bold 15px georgia;  //将按照这个顺序 ：[ [ <' [font-style](font-style.htm) '> || <' [font-variant](font-variant.htm) '> || <' [font-weight](font-weight.htm) '> ]? <' [font-size](font-size.htm) '> [ / <' [line-height](../text/line-height.htm) '> ]? <' [font-family](font-family.htm) '> ] | caption | icon | menu |  message-box | small-caption | status-bar

## day02

```css
/*a标签的第一个背景变成绿色*/
.demo li a:first-child{
		background-color: #0f0;
	}

/*a标签的最后一个背景变成绿色*/
.demo li a:last-child{
		background-color: #0f0;
	}
/*a标签的偶数背景都变成绿色*/
.demo li a:nth-child(2n){
		background-color: #0f0;
	}
/*a标签的每四个变成绿色*/
.demo li a:nth-child(4n){
		background-color: #0f0;
	}
/*首字母下沉变大*/
.demo::first-letter{
			font-size: 40px;
			font-weight: bold;
			float: left;
		}
```



## background-image

background-image: url("../image/1.jpeg"); 

使用时需要配合width 和height一起使用



### box-shadow

### transform

## day03



