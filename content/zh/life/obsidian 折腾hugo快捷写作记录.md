---
title: obsidian 折腾hugo快捷写作记录博客模板 2
date: 2023-11-05T13:00:15+08:00
date created: 星期六, 十一月 4日 2023, 9:22:46 晚上
date modified: 星期日, 十一月 5日 2023, 19:0:316下午:05 晚上
---




设置好仓库后
obsidian 设置

插件
1 . obsidian git   同步
2 . templer,添加时间，官方模板无法支持hugo原生时间格式
故必须使用这个
但也可使用原本模板，但时间不会变
要手动进行修改
```
<% tp.file.creation_date("YYYY-MM-DD[T]HH:mm:ss[+08:00]") %>



```
3 . linter 更新标题
设置新建文件在想要的目录
![image.png](https://cdn.jsdelivr.net/gh/everrwsr/blogimage@master/202311042143428.png)


参考教程
[[Obsidian+Git 完美维护 Hexo 博客]]

[[obsidian 配合 hugo、cloudflare：让发布博客简单到不可思议：：夜猫日记]]

[Obsidian 插件：Templater 可以替代核心模板插件的效率神器](https://pkmer.cn/Pkmer-Docs/10-obsidian/obsidian%E7%A4%BE%E5%8C%BA%E6%8F%92%E4%BB%B6/templater/templater-obsidian/)


