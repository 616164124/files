# css

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

