# 1 初识  HTML

## 1.1 什么是 HTML

HTML：Hyper Text Markup Language（超文本标记语言）

超文本：文字、图片、视频、音频、动画等

## 1.2 W3C 标准

World Wide Web Consourtium（万维网联盟）

成立于1994年，Web技术领域最权威和最具影响力的国际中立性技术标准机构

[w3c](http://w3c.org/)

[w3c中国](http://chinaw3c.org)

### W3C 标准包括

- 结构化标准语言（HTML、XML）
- 表现标准语言（CSS）
- 行为标准（DOM、ECMAScript）

# 2 网页的基本信息

DOCTYPE：告诉浏览器我们要是用什么规范，html是html5的规范

meta标签：描述性标签，一般来做SEO

meta标签的属性：

1. charset：定义文档的字符编码
2. name：context信息属性的名称
3. context：name属性的信息内容

meta标签的案例：

```
<meta name="keywords" content="狂神说Java,西部开源">
<meta name="description" content="来这个地方学习Java">
```

# 3 网页的基本标签

## 3.1 标题标签

h1-h6一共6个级别的标题标签

## 3.2 段落标签

<p>p标签</p> 

## 3.3 换行标签

`<br>` 

## 3.4 水平线标签

`<hr>` 

## 3.5 字体样式标签

`<strong>粗体</strong>` 

`<em>斜体</em>` 

## 3.6 注释和特殊符号

` 空格`

`>大于`

`<小于`

`©版权符`

# 4 图像标签

## 4.1 img 标签

## 4.2 img 标签属性

- src 资源位置
- alt 找不到图像的替代文字
- title 鼠标悬停显示的文字
- width 宽
- height 高

# 5 链接标签

## 5.1 a 标签

## 5.2 属性

- href 跳转
- target 表示窗口在哪里打开， `target="_blank"` 在新标签中打开， `target="_self"` 在本页中打开

## 5.3 锚链接

### 5.3.1 跳转到本页的顶部

```
<a name="top">顶部</a>
...
...
...
<a href="#top">回到顶部</a>
```

### 5.3.2 跳转到其它页面的顶部

```
<a herf="其它页面的路径#top">跳转到其它页面的顶部</a>
```

## 5.4 功能性链接

### 5.4.1 邮件标签

<a  href="mailto:631279832@qq.com">点击右键联系我</a> 

### 5.4.2 qq链接

qq推广

# 6 块内元素和行元素

## 6.1 定义

块内元素：无论内容多少，该元素独占一行

行元素：内容撑开宽度，左右都是行内元素可以排成一行

# 7 列表

## 7.1 什么是列表

列表就是信息资源的一种展示形式。它可以使信息结构化和条理化，并以列表的样式展示出来，以便浏览者能更快捷地获取相应的信息。

## 7.2 列表的分类

无序列表、有序列表、自定义列表

## 7.3 表现形式

### 7.3.1 有序列表

```
<ol>
  <li></li>
</ol>
```

### 7.3.2 无序列表

```
<ul>
  <li></li>
</ul>
```

### 7.3.3 自定义列表

```
<dl>
  <dt>列表标题</dt>
  <dd>列表内容</dd>
</dl>
```

# 8 表格

## 8.1 标签

- table 表格标签
- tr 行标签
- td 列表前

## 8.2 属性

1. table标签

- border 边框

1. td标签

- colspan 跨列，一个td占几列
- rowspan 跨行，一个td占几行

# 9 视频和音频

## 9.1 视频标签 video

## 9.2 音频标签 audio

## 9.3 属性

- src 资源路径
- controls 控制
- autoplay 自动播放

# 10 页面结构分析



| 元素名  | 描述                                               |
| ------- | -------------------------------------------------- |
| header  | 标题头部区域的内容（用于页面或页面中的一块区域）   |
| footer  | 标记脚部区域的内容（用于整个页面或页面的一块区域） |
| section | web页面中的一块独立区域                            |
| article | 独立的文章内容                                     |
| aside   | 相关内容或应用（常用于侧边栏）                     |
| nav     | 导航类辅助内容                                     |

# 11 iframe 内联框架

## 11.1 属性

- src 资源路径
- name 框架标识名
- width 宽
- height 高
- frameborder 边框

## 11.2 其它页面的内容跳到内联框架

```
<iframe src="" name="isme" frameborder="0" width="1000px" height="800px"></iframe>
<a href="https://www.baidu.com" target="isme">点击跳转</a>
```

# 12 初识表单 get 和 post 提交

## 12.1 表单

form 标签

## 12.2 属性

1. form 标签

- method get、post 提交表达的方式
- action 发送表单的地址

1. input 标签

- type 类型 text、password、submit、reset等
- name 名字标识

## 12.3 get 和 post 区别

1. get 可以在url中看到提交的信息，不安全，高效
2. post 安全，可以提交大文件

# 13 文本框和单选框

## 13.1 表单元素格式

| 属性      | 说明                                                         |
| --------- | ------------------------------------------------------------ |
| type      | 指定元素的类型，text、password、checkbox、radio、submit、reset、file、hidden、image、button，默认为text |
| name      | 指定表单元素的名称                                           |
| value     | 元素的初始值，type为radio时，必须指定一个值                  |
| size      | 指定表单元素的初始宽度，当type为text或password时，表单元素大小以字符为单位，对于其它类型表单以像素为单位 |
| maxlength | type 为 text 或 password 时，输入的最大字符数                |
| checked   | type 为 radio 或 checkbox 时，指定按钮是否被选中             |

# 14 按钮和多选框

## 14.1 按钮

```
<input type="button" name="btn1" value="点击">
<input type="image" src="">
<input type="submit">
<input type="reset" value="重置">
```

## 14.2 多选框

```
<input type="checkbox" value="sleep" name="hobby">睡觉
<input type="checkbox" value="coding" name="hobby">编码
<input type="checkbox" value="chat" name="hobby">聊天
```

# 15 列表框文本域和文本域

## 15.1 下拉框

```
<select name=" country">
  <option value="china" selected>中国
  <option value="japan">日本
  <option value="america">美国
</select>
```

## 15.2 文本域

`<textarea name="text" cols="50" rows="10 "></textarea>` 

## 15.3 文件域

`<input type="file" name="files">` 

# 16 搜索框滑块和简单验证

## 16.1 邮箱验证

`<input type="email" name="email">` 

## 16.2 URL 验证

`<input type="url" name="url">` 

## 16.3 数字验证

`<input type="number" name="number" min="0" max="100" step="1">`

## 16.3 滑块

`<input type="range" name="voice" min="0" max="100" step="1">`

## 16.3 搜索框

`<input type="search" name="search">` 

# 17 表单的应用

## 17.1 隐藏域

隐藏属性 hidden

## 17.2 只读

只读属性 readonly

## 17.3 禁用

禁用属性 disabled

## 17.4 增强鼠标可用性

```
<label for="mark">你点我</label>
<input type="text" id="mark"> 
```

# 18 表单初级验证

## 常用方式

1. placeholder 提示信息
2. required value 不能为为空
3. pattern 正则表达式