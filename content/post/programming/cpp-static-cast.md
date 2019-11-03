---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "C++的三种cast"
subtitle: ""
summary: ""
authors: [admin]
tags: [c++]
categories: [programming]
date: 2019-11-01T11:56:25+09:00
lastmod: 2019-11-01T11:56:25+09:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

## 三种cast

在c++有如下三种cast

- static_cast 
- reinterpret_cast 
- dynamic_cast 

在使用过程中有时会有一些疑惑，现在记录下来以供以后回顾查阅

### static_cast

最常用的操作，可以方便的转换各种类型，既可以转换数据的类型，也可以转换指针的类型，一般的应用场景有：

- int->float这样的转换：由于int和float的存储方式（各个bit位表示的内容）不一样，static_cast可以转换内存的layout，使得int的值可以正确的转换成float的值。
- 继承当中base<->derived的互相转换，static_cast保证了转换之后的类指针能够正确的指向对应的内存地址，注意不同类的地址是不同的。
- 注意向下转换是不安全的。

### reinterpret_cast

只是单纯的转换指针类型，并不会做一些内部的转换。类似于先把指针转换为void\*，再把void\*转换为其他类型。

例如：int a=12通过reinterpret_cast转换为float的时候，并不会吧对应内存的layout换成float的表示方法，从而得到的float值并不是12。

### dynamic_cast

通过runtime的检查，保证转换之后的类型的正确性。

## Reference

[What static_cast<> is actually doing]( https://www.codeproject.com/Articles/12935/What-static-cast-is-actually-doing )

