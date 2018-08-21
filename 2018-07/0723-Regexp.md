# 第二章 *示例*

> Perl 相关  
> 1.字符串中可以用变量 $celsius  
> 2.=~ /m/regex/: 匹配正则表达式  
> 3.简写 \s \w \W \d \D  
> 4.修饰符 /i/g  
> 5.(?: )非捕获组  
> 6.`s/regex/replace/` 替换模式

## 例子
1. 替换名字,注意/i: `$var =~ s/\bJeff\b/Jeff/i`
2. 股票价格,只保留2到3位小数: `$price=~ s/(\.\d\d[1-9]?)\d*/$1/g`


## 环视功能(断言/零宽断言)
> 环视不匹配任何字符,只匹配文本中的**特定位置**

- 肯定型顺序环序 <font color=red>**(?=)**</font>  
- 肯定型逆序环序 <font color=red>**(?<=)**</font>  

1. (?=Jeffrey)Jeff   等同于  Jeff(?=rey)
2. Jeffs替换为Jeff's的方法如下:
    -  s/\bJeffs\b/Jeff's/g
    -  s/\b(Jeff)(s)\b/$1'$2/g
    -  s/\bJeff(?=s\b)/Jeff'/g
    -  **s/(?<=Jeff>)(?=s\b)/'/g**
    -  **s/(?=s\b)(?<=\bJeff)/'/g**
3. 千分号(,)的正则: 
    - s/(?<=\d)(?=(?:\d\d\d)+\b)/,/g
    - s/(?<=\d)(?=(?:\d\d\d)+(?!\d))/,/g
5. 单词分界符: `(?<!\w)(?=\w)|(?<=\w)(?!\w)` => \b