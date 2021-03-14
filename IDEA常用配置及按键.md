# IDEA 快捷键/设置

<font color=#ee1111 > 项目开发过程中将.idea文件复制一份，避免在添加内容时产生项目目录错乱的结果</font>



https://zhuanlan.zhihu.com/p/99354824   IDEA 插件推荐安装

https://blog.csdn.net/qq_44695727/article/details/105680530  idea中的设置

1、Ctrl+N按名字搜索类

相当于eclipse的ctrl+shift+R，输入类名可以定位到这个类文件，就像idea在其它的搜索部分的表现一样，搜索类名也能对你所要搜索的内容多个部分进行匹配，而且如果能匹配的自己写的类，优先匹配自己写的类，甚至不是自己写的类也能搜索。

2、Ctrl+Shift+N按文件名搜索文件

同搜索类类似，只不过可以匹配所有类型的文件了。

3、Ctrl+H

查看类的继承关系，例如HashMap的父类是AbstractMap，子类则有一大堆。

4、Ctrl+Alt+B查看子类方法实现

Ctrl+B可以查看父类或父方法定义，但是不如ctrl+鼠标左键方便。但是在这里，Ctrl+B或ctrl+鼠标左键只能看见Map接口的抽象方法put的定义，不是我们想要的，这时候Ctrl+Alt+B就可以查看HashMap的put方法。

5、Alt+F7查找类或方法在哪被使用

相当于eclipse的ctrl+shif+H,但是速度快得多。

6、Ctrl+F/Ctrl+Shift+F按照文本的内容查找

相当于eclipse的ctrl+H，速度优势更加明显。其中Ctrl+F是在本页查找，Ctrl+Shift+F是全局查找。

7、Shift+Shift搜索任何东西

shift+shift非常强大，可搜索类、资源、配置项、方法等，还能搜索路径。其中搜索路径非常实用，例如你写了一个功能叫hello，在java，js，css，jsp中都有hello的文件夹，那我们可以搜索"hello/"找到路径中包含hello的文件夹。

8、查看接口的实现类

IDEA 风格 ctrl + alt +B     或者     Ctrl+Alt+鼠标左键

9、打开service窗口，将下面内容复制到项目中.idea文件夹中的workspace.xml  后重启idea

```<component name="RunDashboard">
 <component name="RunDashboard">
    <option name="configurationTypes">
      <set>
        <option value="SpringBootApplicationConfigurationType" />
      </set>
    </option>
    <option name="ruleStates">
      <list>
        <RuleState>
          <option name="name" value="ConfigurationTypeDashboardGroupingRule" />
        </RuleState>
        <RuleState>
          <option name="name" value="StatusDashboardGroupingRule" />
        </RuleState>
      </list>
    </option>
  </component>
```

## 设置



重要的几点    [参考网址](<https://www.cnblogs.com/pretty-sunshine/p/9967448.html>)

1、将自动编译开关打开

2、忽略大小写开关

3、智能导包开关

4、悬浮提示开关

5、取消单行显示tabs的操作

6、项目文件编码

# vscode

Ctrl+Shift+P,F1 展示全局命令面板

Ctrl+P 快速打开最近打开的文件

Ctrl+Shift+N 打开新的编辑器窗口

Ctrl+Shift+W 关闭编辑器

Ctrl + X 剪切

Ctrl + C 复制

Alt + up/down 移动行上下

Shift + Alt up/down 在当前行上下复制当前行

Ctrl + Shift + K 删除行

Ctrl + Enter 在当前行下插入新的一行

Ctrl + Shift + Enter 在当前行上插入新的一行

Ctrl + Shift + | 匹配花括号的闭合处，跳转

Ctrl + ] 或 [ 行缩进

Home 光标跳转到行头

End 光标跳转到行尾

Ctrl + Home 跳转到页头

Ctrl + End 跳转到页尾

Ctrl + up/down 行视图上下偏移

Alt + PgUp/PgDown 屏视图上下偏移

Ctrl + Shift + [ 折叠区域代码

Ctrl + Shift + ] 展开区域代码

Ctrl + / 添加关闭行注释

Shift + Alt +A 块区域注释

Alt + Z 添加关闭词汇包含

**导航快捷键**

Ctrl + T 列出所有符号

Ctrl + G 跳转行

Ctrl + P 跳转文件

Ctrl + Shift + O 跳转到符号处

Ctrl + Shift + M 或 Ctrl + J 打开问题展示面板

F8 跳转到下一个错误或者警告

Shift + F8 跳转到上一个错误或者警告

Ctrl + Shift + Tab 切换到最近打开的文件

Alt + left / right 向后、向前

Ctrl + M 进入用Tab来移动焦点

Ctrl + F 查询

Ctrl + H 替换

F3 / Shift + F3 查询下一个/上一个

Alt + Enter 选中所有出现在查询中的

Ctrl + D 匹配当前选中的词汇或者行，再次选中-可操作

**多行光标快捷键**

Alt + Click 插入光标-支持多个

Ctrl + Alt + up/down 上下插入光标-支持多个

Ctrl + U 撤销最后一次光标操作

Shift + Alt + I 插入光标到选中范围内所有行结束符

Ctrl + I 选中当前行

Ctrl + Shift + L 选择所有出现在当前选中的行-操作

Ctrl + F2 选择所有出现在当前选中的词汇-操作

Shift + Alt + right 从光标处扩展选中全行

Shift + Alt + left 收缩选择区域

Shift + Alt + (drag mouse) 鼠标拖动区域，同时在多个行结束符插入光标

Ctrl + Shift + Alt + (Arrow Key) 也是插入多行光标的[方向键控制]

Ctrl + Shift + Alt + PgUp/PgDown 也是插入多行光标的[整屏生效]

Esc Esc 连续按两次Esc键取消多行光标

Shift + Alt + F 格式化代码

F12 跳转到定义处

Alt + F12 代码片段显示定义

Ctrl + K F12 在其他窗口打开定义处

Ctrl + . 快速修复部分可以修复的语法错误

Shift + F12 显示所有引用

F2 重命名符号

Ctrl + Shift + . / , 替换下个值

**编辑器管理快捷键**

Ctrl + F4, Ctrl + W 关闭编辑器

Ctrl + |切割编辑窗口

Ctrl + 1/2/3 切换焦点在不同的切割窗口

Ctrl + Shift + PgUp/PgDown 切换标签页的位置

**文件管理快捷键**

Ctrl + N 新建文件

Ctrl + O 打开文件

Ctrl + S 保存文件

Ctrl + Shift + S 另存为

Ctrl + F4 关闭当前编辑窗口

Ctrl + W 关闭所有编辑窗口

Ctrl + Shift + T 撤销最近关闭的一个文件编辑窗口

Ctrl + Enter 保持开启

Ctrl + Shift + Tab 调出最近打开的文件列表，重复按会切换

Ctrl + Tab 与上面一致，顺序不一致

Ctrl + P 复制当前打开文件的存放路径

Ctrl + R 打开当前编辑文件存放位置【文件管理器】

**显示快捷键**

F11 切换全屏模式

Ctrl + =/- 放大 / 缩小

Ctrl + B 侧边栏显示隐藏

Ctrl + Shift + E 资源视图和编辑视图的焦点切换

Ctrl + Shift + F 打开全局搜索

Ctrl + Shift + G 打开Git可视管理

Ctrl + Shift + D 打开DeBug面板

Ctrl + Shift + X 打开插件市场面板

Ctrl + Shift + H 在当前文件替换查询替换

Ctrl + Shift + J 开启详细查询

Ctrl + Shift + V 预览Markdown文件【编译后】

Ctrl + K v 在边栏打开渲染后的视图【新建】

**调试快捷键**

F9 添加解除断点

F5 启动调试、继续

F11 / Shift + F11 单步进入 / 单步跳出

F10 单步跳过

**集成终端快捷键**

Ctrl + ` 打开集成终端

Ctrl + Shift + ` 创建一个新的终端

Ctrl + C 复制所选

Ctrl + V 复制到当前激活的终端

Shift + PgUp / PgDown 页面上下翻屏

Ctrl + Home / End 滚动到页面头部或尾部





## 配置

1.vscode在编写Vue文件时报红色波浪线之解决方法：

vscode-->文件-->首选项-->设置-->直接搜索eslint.enable 将选项去掉

