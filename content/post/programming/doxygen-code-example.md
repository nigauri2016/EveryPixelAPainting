---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Doxygen Code Example"
subtitle: ""
summary: ""
authors: [admin]
tags: []
categories: []
date: 2019-08-15T14:41:28+08:00
lastmod: 2019-08-15T14:41:28+08:00
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

# Doxygen的c++代码注释

这里总结一下自己的C++注释风格，以供查阅使用

1. 所有的注释使用c++风格的`///`开头，在header尽量使用brief的注释，在source使用detailed的注释。

2. 所有doxygen的标记都是用`\`来标记。

3. 若声明和定义都在header，或者是class的声明，则所有的注释都在header

   ```c++
   /// \brief A brief class description. 
   /// 
   /// A detailed class description, it
   /// should be 2 lines at least
   class MyClass
   {
       
   }
   ```

4. 文件的注释：source和header都需要加上文件的注释，在所有代码之前，如：

   ```c++
   /// \file ClassHeader.h
   /// \brief Head file for class Ctest.
   /// 
   /// A detailed file description.
   ///
   /// \author author_name
   /// \version version_number
   /// \date xxxx-xx-xxx
   ```

5. namespace的注释，在header是brief，在source是detailed。namespace的注释一般只需要写一次。

6. Constructor和class variable的注释，在header是brief或者普通注释，在source是detailed的注释。

   ```c++
   //header.h 
   class  MyClass
    {
           public:
               /// \brief brief constructor description. 
               MyClass();
   
               /// class variable description
               int PublicVariable; 
     }
   
   //source.cpp   
      /// constructor detailed defintion, 
      /// should be 2 lines
      MyClass::MyClass()
        :PublicVariable(10)
      {
   
      }
   ```

7. 类方法的注释，在header是brief的注释加上参数返回值的注释，在source是detailed的注释

   ```c++
   //header.h
   public:
      /// \brief A brief function description. 
      ///
      /// \param p1 Description for p1.
      /// \param p2 Description for p2.
      /// \return Description for return value.
      int GetVariable(int p1, float p2);
   
   //source.cpp
      /// A detailed function description, it
      /// should be 2 lines at least.
      int MyClass::GetVariable(int p1, float p2)
      {
          return 1;
      }
   ```

8. 另外有\bug, \note, \todo 等标记可以使用

## Example Code

- https://github.com/nigauri2016/DoxygenExample