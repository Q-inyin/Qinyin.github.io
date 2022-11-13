---
title: 预处理css
date: 2022-08-27 23:47:19
categories: ['html+css']
tags: ['分享','css']
---

## CSS-Less

Less is a dynamic preprocessor style sheet language that can be compiled into Cascading Style Sheets and run on the client side or server side. Designed by Alexis Sellier, Less is influenced by Sass and has influenced the newer "SCSS" syntax of Sass, which adapted its CSS-like block formatting syntax. --Wikipedia

Less是一种动态的预处理器样式表语言，可以将其编译成级联样式表并在客户端或服务器端运行。 由Alexis Sellier设计的less受Sass的影响，并影响了SASS的较新的“ SCSS”语法，该语法适用于其CSS式的块格式语法。

**简单地说：less就是简便书写css的工具，还是像写css那样写，只是有些比较简洁，可以写除法、选择器套选择器等等。保存.less文件，就会在同级别下自动生成.css文件。**

**Node中使用**
```
npm install -g less
> lessc styles.less styles.css
```
**游览器中使用**
```
<link rel="stylesheet/less" type="text/css" href="styles.less" />
<script src="https://cdn.jsdelivr.net/npm/less" ></script>
```

## 变量
```
'@buttonFace': '#5B83AD',
'@buttonText': '#D9EEF2'

#header {
  color: @buttonFace;
  background-color: @buttonText;
}

##结果

#header {
  color: #5B83AD;
  background-color: #D9EEF2;
    }
```
## 嵌套
```
#header {
  color: black;
}
#header .navigation {
  font-size: 12px;
}
#header .logo {
  width: 300px;
}

##结果

#header {
  color: black;
  .navigation {
    font-size: 12px;
  }
  .logo {
    width: 300px;
  }
}
```
## 映射
```
#main {
    @media screen {
        @media (max-width:437px){
            width:50px;
        }
    }
}

##结果

@meida screen and (max-width:437px){
    main {
        width:50px;
    }
}
```