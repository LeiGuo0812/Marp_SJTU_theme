---
marp: true
size: 16:9
---
<!-- _paginate: false -->
<style scoped>
section {
    background-color: #224466;
    color: white;
    text-align: center;
    font-size: 1.5cm;
}
h1 {
    color: white;
    text-align: center;
    font-size: 2cm;
}
</style>

# Marp 使用指南
郭垒

---
<!-- header: ![w:50](133.png) -->
<!-- paginate: true -->

# Marp 使用指南

参考：[知乎链接](https://www.zhihu.com/question/35164931/answer/2248596656?utm_source=wechat_session&utm_medium=social&s_r=0)

## 1. 安装

</br>

- **vscode**
- 插件：**markdwon all in one**
- 插件：**marp for vscode**

---
# 2. 创建一个marp文档

- 创建 `.md`文件

- 激活marp

在最上层输入YAML语法：
```yaml
---
marp: true
---
```
即可激活marp的功能

---
# 3. 分页
```
---
```
</br>

- 插入`---`进行分页

- `---`上一行需要空出来

---
# 4. Marp指令 (Directives)

## YAML front matter

添加在最前面的YAML代码中

```yaml
---
theme: default
paginate: true
---
```

此处的指令会在全局生效

---

# 指令类型

## 全局指令
在每个silde的指令前加`$`的方式已经被弃用，可以在YAML代码中定义

## 局部指令
- 使用 `<!-- _directive: value -->` 指定局部指令（指令前加下划线`_`），位置要放在该页slide分隔符后面，只对当前幻灯片生效

- 使用`<!-- directive: value -->`，命令对当前页和之后的页生效


---
# 全局指令

|命令            |作用                  |
|----------------|---------------------|
| `theme`          | 指定幻灯片的主题。    |
| `style`         | 指定 CSS 来调整主题。 |
|`headingDivider` | 指定标题分隔符选项。  |

</br>

`theme`指定主题，可选的有 `default`, `gaia`, `uncover`
</br>

`headingDivider`指定是否用一级标题作为幻灯片分割，默认是`false` 在从原生Markdown文件生成PPT时比较有用

---
# 全局指令

`style`  调整主题

```yaml
---
theme: base-theme
style: |
  section {
    background-color: #ccc;
  }
---
```

---
# 本地指令
|命令|作用|
|---|---|
|`paginate`|如果设置了true，则在幻灯片上显示页码。|
|`header`|指定幻灯片标题的内容。|
|`footer`|指定幻灯片页脚的内容。|
|`class`|`<section>`指定幻灯片元素的 HTML 类。|
|`backgroundColor`|幻灯片的设置`background-color`样式。|
|`backgroundImage`|幻灯片的设置`background-image`样式。|
|`backgroundPosition`|幻灯片的设置`background-position`样式。|
|`backgroundRepeat`|幻灯片的设置`background-repeat`样式。|
|`backgroundSize`|幻灯片的设置`background-size`样式。|
|`color`|幻灯片的设置color样式。|

---
<!-- _class: lead -->

# 本地指令

本地指令可以在YAML进行全局设置，也可以在slide命令里进行本地设置

`header` 和 `footer`可以指定页眉页脚，也可以使用`Markdwon`语法对文字格式化，也可以使用Marp图片语法插入图片

```yaml
---
header: '**bold** _italic_'
footer: '![image](https://example.com/image.jpg)'
---

NOTE: Wrap by (double-)quotes to avoid parsed as invalid YAML.
```
---

# 本地指令

用`backgroundColor`或`backgroundImage`定义幻灯片的背景图片或颜色，也可以用渐进色

`color`定义文本颜色

```yaml
<!-- backgroundImage: "linear-gradient(to bottom, #67b8e3, #0288d1)" -->

Gradient background

---

<!--
_backgroundColor: black
_color: white
-->

Black background + White text
```
---

# 5. 图片语法
Marpit 扩展了 Markdown 图像语法`![](image.jpg)`以帮助创建漂亮的幻灯片。 

## 图像大小调整
用`weight`和`height`指定图像的长宽
```yaml
![width:200px](image.jpg) <!-- Setting width to 200px -->
![height:30cm](image.jpg) <!-- Setting height to 300px -->
![width:200px height:30cm](image.jpg) <!-- Setting both lengths -->
```
用 `w`和`h`简写

```yaml
![w:32 h:32](image.jpg) <!-- Setting size to 32x32 px -->
```

---

## 图片滤镜

|Markdown | w/ arguments|
|---|---|
|`![blur]() `| `![blur:10px]()`|
|`![brightness]()` | `![brightness:1.5]()`|
|`![contrast]()` | `![contrast:200%]()`|
|`![drop-shadow]()` | `![drop-shadow:0,5px,10px,rgba(0,0,0,.4)]()`|
|`![grayscale]()` | `![grayscale:1]()`|
|`![hue-rotate]()` | `![hue-rotate:180deg]()`|
|`![invert]()` | `![invert:100%]()`|
|`![opacity]() `| `![opacity:.5]()`|
|`![saturate]()` | `![saturate:2.0]()`|
|`![sepia]()` | `![sepia:1.0]()`|

指定多重滤镜
```yaml
![brightness:.8 sepia:50%](https://example.com/image.jpg)
```

---
## 背景图片
语法为 `![bg keyword](imag.jpg)`，`kdyword`设置背景的嵌入方式

|Keyword|Description|Example|
|---|---|---|
|cover|Scale image to fill the slide. (Default)|`![bg cover](image.jpg)`|
|contain|Scale image to fit the slide.|`![bg contain](image.jpg)`|
|fit|Alias to contain, compatible with Deckset.|`![bg fit](image.jpg)`|
|auto|Not scale image, and use the original size.|`![bg auto](image.jpg)`|
|x%|Specify the scaling factor by percentage value.|`![bg 150%](image.jpg)`|

---
## 进阶背景

### 多重背景

横向排列
```
![bg](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
![bg](https://fakeimg.pl/800x600/02669d/fff/?text=B)
![bg](https://fakeimg.pl/800x600/67b8e3/fff/?text=C)
```
![bg](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
![bg](https://fakeimg.pl/800x600/02669d/fff/?text=B)
![bg](https://fakeimg.pl/800x600/67b8e3/fff/?text=C)

---

### 多重背景

纵向排列
```
![bg vertical](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
![bg](https://fakeimg.pl/800x600/02669d/fff/?text=B)
![bg](https://fakeimg.pl/800x600/67b8e3/fff/?text=C)
```
![bg vertical](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
![bg](https://fakeimg.pl/800x600/02669d/fff/?text=B)
![bg](https://fakeimg.pl/800x600/67b8e3/fff/?text=C)

---

### 背景分割
```
![bg left](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
```
![bg left](https://fakeimg.pl/800x600/0288d1/fff/?text=A)

---

### 背景分割 + 多重背景
```
![bg vertical right](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
![bg](https://fakeimg.pl/800x600/02669d/fff/?text=B)
```
![bg vertical right](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
![bg](https://fakeimg.pl/800x600/02669d/fff/?text=B)

---

### 背景分割大小
```
![bg left:10%](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
```
![bg left:10%](https://fakeimg.pl/800x600/0288d1/fff/?text=A)

---
### 背景分割大小
```
![bg right vertical w:10cm](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
![bg right w:5cm](https://fakeimg.pl/800x600/0288d1/fff/?text=B)
```
![bg right vertical w:10cm](https://fakeimg.pl/800x600/0288d1/fff/?text=A)
![bg right w:5cm](https://fakeimg.pl/800x600/0288d1/fff/?text=B)

---
# 6.设置颜色的简单语法

通过 Markdown 图像语法，Marpit 允许定义颜色值而不是图像 URL。

```
![bg](#fff)
![](#000)
```
![bg](#fff)
![](#000)

---

# 6.设置颜色的简单语法

颜色名设置
```
![bg](rebeccapurple)
![](orange)
```
![bg](rebeccapurple)
![](orange)

---

# 6.设置颜色的简单语法

使用RGB定义颜色
```
![bg](rgb(255,128,0))
![](rgb(255,255,255))
```
![bg](rgb(255,128,0))
![](rgb(255,255,255))

---
# 7. 列表

# Bullet list: 所有内容同时呈现
```
- One
- Two
- Three
```
- One
- Two
- Three
---

# Fragmented list: 内容依次呈现
```
* One
* Two
* Three
```
* One
* Two
* Three

---

# Ordered list: 内容同时呈现
```
1. One
2. Two
3. Three
```
1. One
2. Two
3. Three

---

# Fragmented list：内容依次呈现
```
1) One
2) Two
3) Three
```
1) One
2) Two
3) Three

---
# 8. style设置

全局style: 放在任意页都可以

```html
<style>
section {
  background: #aaa;
  color: white;
  font-size: 0.6cm;
}
h1 {
    color: white;
    font-size: 2cm;
}
h2 {
    color: yellow
}
h3 {
    color: green
}
h4 {
    color: blue
}
h5 {
    color: red
}
</style>
```

---
局部style
```html
<style scoped>
section {
  background: black;
}
h1 {
    color: lightskyblue;
    font-size: 2cm;
}
h3 {
    color: white
}
</style>
```
---
定义全局局部引用

```html
<style>
section.bg {
  background: black;
}
section.bg h1 {
    color: red;
    font-size: 2cm;
    text-align: center;
}
section.bg h3 {
    color: white
}
</style>
- 引用:`<!-- _class: bg -->`
```
在`class`中设置`bg`即可使用 `section.bg`的style

