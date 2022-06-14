# Marp_SJTU_theme

## 使用方法

- 创建一个新文件夹
- 在新文件夹下创建 marp的 .md 文档
- vscode打开，设置目录为该文件夹
- 在marp的YAML语句中指定`theme: SJTU`

## 如何修改
- 打开css文件
- 修改主题名字：`/* @theme SJTU */`
- 修改母模板：`@import 'default';`,可用的有 `default`, `gaia` 和 `uncover` 三种
- 修改字体：`@import url('谷歌字体库导出网站');`,然后在各个层级标题设置具体的字体，设置所需名称参考谷歌字体网站
- 修改其他元素：参考css文件语法修改

## 参考链接
[https://github.com/BeWaterMyFriend7/Marp-Theme-UCAS](https://github.com/BeWaterMyFriend7/Marp-Theme-UCAS)

[https://zhuanlan.zhihu.com/p/449668027](https://zhuanlan.zhihu.com/p/449668027)

[https://zhuanlan.zhihu.com/p/449668027](https://zhuanlan.zhihu.com/p/449668027)
