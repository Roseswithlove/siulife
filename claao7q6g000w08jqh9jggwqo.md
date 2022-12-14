# 从 Typecho 迁移到 Eleventy

这个博客由 Typecho 提供支持将近 3 年后，它现在是一个使用 <a href="https://www.11ty.dev/">Eleventy</a> 构建的静态生成的网站。

目前博客也不再是自己买云服务器托管了，它现在托管在 <a href="https://www.cloudflare.com/">Cloudflare</a>/<a href="https://www.github.com/">Github</a> 上，这个网站现在又给我省了一件事，那就是备份。

## 为什么选择 Eleventy？

在我第一次看到 <a href="https://www.11ty.dev/">Eleventy</a> 是在 <a href="https://www.200011.net/">油油大佬</a> 的博客。<a href="https://www.11ty.dev/">Eleventy</a> 引起了我的兴趣，因为感觉它非常容易上手。根本不需要学习太多，文档简洁实用。基本上在搭建时，<a href="https://www.11ty.dev/">Eleventy</a> 将解释 Markdown 文件并将它们转换为语义 html 文档。您可以在这些模板周围安装模板。

## 创建站点

现在第一件事就是生成一个没有数据的 <a href="https://www.11ty.dev/">Eleventy</a> 的站点。

```
mkdir blog
cd blog
npm init -y
npm install @11ty/eleventy
code .
```

然后选择package.json这个文件，编辑一下scripts这个部分的，删除test那段代码，添加下面这段代码

```
"start": eleventy --serve
```

保存之后，打开终端，输入这段命令启动本地网页服务器
```
npm run start
```

之后打开浏览器在地址那输入 http://localhost:8080

你就会看到一段 Cannot GET /
然后再根目录新增一个新文件 index.md 里面写段
```
# hello world
```

切换到浏览器 刷新一下 如果出现下面这段话
太好了，说明一切正常！

![](https://img.mukewang.com/user/6108a18c0001867904290175.jpg)

在根目录再新建一个名为 eleventy.js 的文件 
这是一个 11ty 的项目设定文件

src：存网页相关文件的文件夹

dist：输出静态html的文件夹

includes：存放主题模板的文件夹

```
module.exports = (eleventyConfig) => {
    return {
        dir: {
            input: 'src',
            output: 'dist',
            includes: '_includes'
        },
        markdownTemplateEngine: 'njk'
    }
}
```

在src文件夹下面再新增两个_includes和_data文件夹后

在_includes里再新增一个layouts的文件夹

在layouts文件夹新增一个名叫base.njk的文件（base.njk 可以说是一个主题模板）

_data文件夹是存放一些数据比如导航之类的

<blockquote>
哦，对了不懂也可以看一下<a href="https://www.11ty.dev/blog/"> Eleventy官方文档 </a> ！
</blockquote>

## 那我怎么写文章呢？

弄完上面这些操作后，在src里新增一个分类文件夹，我这里名为blog，这个文件夹是用来存放你写的md文章

```
---
layout: 'layouts/base.njk' 这里是引用模板
tags: blog
title: 文章名字
data: 日期
---
```

## 最后

<a href="https://www.11ty.dev/">Eleventy</a> 大致就是这个样子，等你弄完所有东西，把dist目录下的文件上传到 <a href="https://www.cloudflare.com/">Cloudflare</a>/<a href="https://www.github.com/">Github</a> 上就大功告成了，为什么我不继续用 <a href="http://typecho.org/">Typecho</a> 呢？还不是因为没钱买云服务器，<a href="http://typecho.org/">Typecho</a> 也是一款轻量高效，稳定，简洁友好的一款博客程序。

但使用使用 <a href="https://www.11ty.dev/">Eleventy</a> 搭建的网站可以让我很省心省钱，并拥有一个快速、轻量级的网站，使用起来还是和 <a href="http://typecho.org/">Typecho</a> 一样很愉快。