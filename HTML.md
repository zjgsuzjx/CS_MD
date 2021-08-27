> 💥此MD/PDF/HTML文档由 [@竹梦者也]([竹梦者也 - ZJXのBLOG (zjgsuzjx.top)](https://www.zjgsuzjx.top/)) 编辑制作，不可转载❌、打印❌、二次编辑❌、贩卖❌。仅供学习交流使用，下载后切勿随意传播。
>
> 📌欢迎在留言区提供修改建议~
>
> 
>
> ✅2021.6.22	 @竹梦者也(https://www.zjgsuzjx.top) 





## 一、HTML简介

### 一、网页

1. 网站=n个网页，网页文件以.html或.htm结尾，网页由图片、链接等多个元素组成。
2. HTML指的是超文本标记语言，不是编程语言，而是一种标记语言。
3. 所谓超文本：1.可以加入图片、音乐等内容。2.可以从一个文件跳转到另一个文件。

### 二、常用浏览器

浏览器是网页显示、运行的平台。常用的浏览器有 IE、火狐（Firefox）、谷歌（Chrome）、Safari和Opera等。
平时称为五大浏览器。

浏览器内核负责读取网页内容，计算网页的显示方式并显示页面。（代码转视觉页面的关键）

### 三、web标准

##### Web标准的构成

web标准，规范浏览器的行为。主要由结构（html）、表现（css）、行为（JavaScript）三个封面。最佳解决方案为：结构、样式、行为相分离。

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/2b32dcd1f98b05b25e8d0c2f43a4802c.png)

> 结构更加重要，相当于肉体。

## 二、HTML标签

### 一、HTML语法规范

**标签：**`<html></html>`   一般是成对出现的，称为<u>双标签</u>，结束标签有反斜杠。而<br/>为<u>单标签</u>。

**标签关系：**

- 包含关系

  ```html
  <head>
     <title></title>
  </head>
  ```

- 并列关系

  ```html
  <head></head>
  <body></body>
  ```

> 注：html页面又称为html文档

### 二、HTML基本结构标签

```html
<html></html>      HTML标签，又称根标签

<head></head>  文档的头部

<title> </title>   文档的头部，相当于网页标题

<body></body>  文档的主体
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/6d725c8613efe081e11c2ba4a26abbd7.png)

要记住各个结构标签之间的关系，正常逻辑如下：

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/e4aa44bb76e2adc03c82eb2a23375e7a.png)

### 三、开发工具

常用的开发工具：webstorm，DW cs6，vscode（常用）

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/7d9e5b8b8c8cb84f113224575b8e3dac.png)

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/c09afa505af32ba4625ffaa3ba98a2ac.png)

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/14c7c8c920e57933a8057cc498d36f85.png)

#### 总结

- `<!DOCTYPE>`：文档类型声明标签，作用是告诉浏览器使用的html版本。
- `<!DOCTYPE html>`，这句代码意思是采用的是HTML5版本来显示网页。**必须写在第一行。**
- `<html lang="en">`：定义当前文档显示的语言，`zh-CN`是中文，`en`是英文。内容中没有严格要求中英文，只是起提示作用，谷歌浏览器会显示是否要翻译。
- `<meta charset="UTF-8">`：用来以某个特定属性来存储文字。UTF-8最常用，也被称为万国码，以防止出现乱码。**一定要写。**

### 四、HTML 常用标签

#### 1. 标签语义

在合适的地方给一个合理的标签，可以让页面结构更加清晰。

#### 2. 标题标签

```
<h1>---<h6>，重要程度依次减小。
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/f55d7832518fba6964feb143a4df5b4e.png)

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/bf48997bfce0322696d2d9d28e5cba56.png)

#### 3. 段落标签

```
<p></p>，paragraph，可以把html文档分割成若干段落。
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/381c9b8a9f9ddd7c41825177a00770cb.png)

**换行标签：**<br />，break。强制换行。也可以写<br>

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/6050ea545469b5cf7ad45d9503b350bb.png)

段落和换行的垂直距离不一样。

#### 4. 文本格式化标签

添加粗体、斜体、下划线达到。使得以特殊的方式显示。

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/68d2dc86fdc122d9f3437eb9e22199ad.png)

####  5. div和span标签

```
<div></div>、<span></span>是盒子，没有语义，用来装内容的。div是division，表示分割。span意为跨度、跨距。
```

`<div>`是单独占领一行。`<span>`是一个小盒子，一行能放多个`span`。

#### 6. 图像标签和路径

```
<img src="图像URL"  />，是单标签。
```

src是必须属性，用于指定图像文件的路径和文件名。

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/391f4d4adc2a553b72c0ed1306ba5e0a.png)

```
如：<img src="1.jpg"  alt="无法显示" title="我是标题"   width="500"    height="100" border="15"   />，可以不加反斜杠。
```

> 注意：border一般在css里设定

属性之间不分次序，但是标签名必须放在最前面。属性采取键值对的形式。

目标文件夹与根目录的区别。目标文件夹的第一层就是根目录。

**绝对路径：**是指目录下的绝对位置，直接到达目标位置。

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/db11f0dee86bb2e056258ea5e0959638.png)

**相对路径：**图片相对于HTML页面的位置。

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/093e03aa31a565882c0d044d81f27a35.png)

#### 7. 超链接标签

从一个页面链接到另一个页面

```
<a href="跳转目标"  target="目标窗口的弹出方式">文字或图像</a>，默认是_self打开新页面  a=anchor，喵
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/5ce7938cb37694fba0acf6b069525bb8.png)

**外部链接：**必须以http://开头，链接外部网站

**内部链接：**网站内部的链接，直接链接文件名字就行。如href=“index.html”

**空链接：**

```
<a href="#">空白</a>
```

**下载链接：**地址链接是文件.exe或压缩表.zip等.

**网页元素链接：**图片、音频、视频都可以添加超链接，如：

```html
<a href="https://www.baidu.com"><img src="img.jpg"></a>
```

**瞄点链接：**点击链接时，会快速跳转到页面某个位置，如：

```html
<a href="#名字">example</a>
<h3 id="名字">zjx</h3>
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/02ccb1bd6901e1dd45685e209f29aa64.png)

### 五、HTML中的注释和特殊字符

**注释标签**：用来理解，不会显示在页面上。

<!--xxxxxxxxx-->，**快捷键ctrl+/**

**特殊字符：**一些特殊符号很难使用，如空格

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/17a5db9a5d807b68e96850c6de8abdd3.png)

### 六、表格标签

用于显示、展示数据。

```html
<table>
      <tr>
         <td></td>
         <td></td>
         <td></td>
      </tr>
</table>
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/7efd1ef195c61cea540121344486b39e.png)

####  1. 表头单元格标签

将单元格内的文本内容加粗并居中显示。`<th></th>`

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/11fb81f1c0ead34ac051cad7285f39fd.png)

#### 2. 表格属性

这些属性要写到`<table>`里

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/57d5a52e0ca505933e272b8870cca2f6.png)

#### 3. 表格结构标签

用来分清表格头部和表格主体两大部分。`<thead>`表示表格头部。`<tbody>`表示表格主体。

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/4f36f19361d1ec3b7014a745c2b6d830.png)

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/c60e369afca6d74d17f9562d250a5f96.png)

#### 4. 合并单元格

跨行合并：rowspan="单元格个数"，最上面单元格为目标单元格

跨列合并：colspan="单元格个数"，最左边单元格为目标单元格。

如`<td colspan="2"></td>`

之后要删除多余的单元格。

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/75fc9618dd5e93a9f58dd60f93ad2bc7.png)

### 七、列表标签

用来布局的。

无序列表（重要）、有序列表、自定义列表

#### 1. 无序列表

```
<ul>表示无序，<li>表示列表项
```

如：

```html
<ul>
    <li></li>
    <li></li>
</ul>
```

```
<ul>只能放<li>，而<li>可以放任何标签。
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/6d004dcebf4575de762d7633e715a9d2.png)

#### 2. 有序列表

```
<ol>表示有序。会自动加上1 2 3
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/a557e21211917ae643101c229c79034f.png)

#### 3. 自定义列表

常用于解释术语。

```
<dl>表示自定义列表，<dt>为定义项目，<dd>为解释说明。
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/3f0225b8d96e682cb2f456661c06332a.png)

### 八、表单标签

类似调查问卷、注册账号，用于收集用户信息。

由表单域、表单控件、提示信息组成。

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/6d96313931d9a50b3416d5732f85bc7d.png)

#### 1. 表单域

可以把信息送到服务器。

```html
<form action="url地址" method="提交方式"  name="表单域名称">各种表单元素控件</form>
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/89be52341d36f52b3be03a9680f7fc6f.png)

#### 2. 表单控件

##### 2.1 input表单元素

实现用户与页面的交互

`<input type="属性值"	/>`，是单标签，属性值可以是text、password等

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/85187b959a1bf11069d15344207a7c0f.png)

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/0246e141c7752f01fca1e5cd9d941abf.png)

> 对于radio`类型`，给表单元素加上相同的名字，即`name="sex"`，才能给单选按钮实现多选一。

`value`是元素的真正值。`checked`是给单选框或多选框默认值。maxlength为最大长度。

> `button`类型配合JS使用。file类型用来上传文件。

##### 2.2 label标签

用来绑定一个表单元素，点击label标签内的文本时，浏览器会自动选择对应的表单元素上，用来增加用户体验。

如：

```html
<label for="xxx">用户名：</label>
<input type="text" id="xxx">
```

> for和id的内容要一样。

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/c5fde4ae9dc02497c819d046b06f5715.png)

##### 2.3 select下拉表单元素

```html
<select>
    <option></option>
    <option selected="selected"></option>
    <option></option>
</select>
```

![img](https://img.zjgsuzjx.top/img/images/2021/06/08/f03a9ad436762dd9f701bfb36d66f3b7.png)

##### 2.4 textarea输入大量内容

常见于留言板。

```html
<textarea   rows=""     cols="">文本内容</textarea>
```

cols=“每行中的字符数” ，rows=“显示的行数”，我们在实际开发中不会使用，都是用 CSS 来改变大小。

#### 3. 表单元素总结

有三个名字非常相似的标签:

 (1) 表单域 `form` 使用场景: 提交区域内表单元素给后台服务器

 (2) 文件域 `file` 是input type 属性值 使用场景: 上传文件

 (3) 文本域 `textarea` 使用场景: 可以输入多行文字, 比如留言板 网站介绍等

> 我们当前阶段不需要提交表单元素,所以我们只负责表单元素的外观形态即可.

### 九、查阅文档

百度：www.baidu.com

W3C：www.w3school.com.cn

MDN: developor.mozilla.org/zh-CN/