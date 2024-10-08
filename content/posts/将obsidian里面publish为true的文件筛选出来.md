---
cards-deck: Default
createAt: 2024-10-07 16:37:19
createDate:
- - 2024-10-07
draft: true
publish: true
title: "\u5C06obsidian\u91CC\u9762publish\u4E3Atrue\u7684\u6587\u4EF6\u7B5B\u9009\u51FA\
  \u6765"
updateAt: 2024-10-07 16:37:19
---

tags:

先解析 obsidian 里面 md 文件的 yaml 的内容。
![Pasted image 20241007163747.png](/images/Pasted image 20241007163747.png)

非常好，已经可以了，但是现在有个问题，我需要将这些文件筛选出来之后复制到当前的 blog 的文件夹中，如果没有就新建一个文件夹，文件夹名是当前日期时间字符串去掉中间符号只保留数字的文本。

非常好，又实现了一个功能，我是要将 blog 文件夹里面的 md 通过 hexo 静态博客工具发布到互联网上的，但是现在 blog 里面的 md 文件有个问题，里面的内容如果是附件内容无法正常展示，因为 obsidian 的附件格式是![附件名](/images/附件名)这种格式，这个附件也在当前文件夹中，也需要递归找到并且复制到之前的新建的文件夹中

````
## Embed an image in a note 

To embed an image:

```md
![Engelbart.jpg](/images/Engelbart.jpg)
````

```

```

非常好，又解决了一个问题, 文件已经复制过去了，现在又发现了一个文件，markdown 的标准语法是无法解析 obsidian 的附件![附件名](/images/附件名)这种格式的内容的，需要将这种格式转化成标准的 markdown 的语法，请基于已经将源文件和附件文件都在同一个文件夹下前提，修改下 blog 文件中的 md 文件。

搞错了，附件要在另外的 image 文件夹下，而不是源文件和附件文件都在同一个文件夹下。需要你重新修改下
