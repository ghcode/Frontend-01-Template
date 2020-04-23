* BNF（产生式）

  * 定义语言的组成集合

* 图灵完备性

  * 命令式

    * goto
    * if和while

  * 声明式-lambda

    * 递归

    [注] sql属于非图灵完备

* 动态与静态-错误产生的环境来区分(运行时和编译时)

* 类型系统

  * 动态类型与静态类型
  * 强类型与弱类型
    * 有隐式转换的类型式弱类型
  * 复合类型
    * 结构体  class（组织基本类型形成新的类型）
    * 函数签名  TS函数声明
  * 子类型
    * 逆变/协变
      * 逆变   子类型变量=父类型实例
      * 协变   父类型变量=子类型实例

* 一般命令式编程语言的组成

  * atom
  * expression
  * statement
  * structure
  * program

* javascript的组成

  * atom

    * 码点 ： 一个码点是信息原子的单元。文本是一连串的码点。每一个码点是一个由标准的Unicode编码规定的数字。

    * unicode

      * unicode blocks(分组)
        * ascil
        * cjk
      * Unicode Character Categories(类别)

    * js语法

      * 词法
      * 语法

    * InputElement（书写js代码可以使用的字符集合规范）

      * whitespace

      * LineTerminal

      * Comment

      * Token

        * number

        * string

          * > ```javascript
            > /*
            > 	BMP:基本多文种平面，BMP(Basic Multilingual Plane)，或称第零平面(Plane 0)，是Unicode中的一个编码区段。编码从U+0000至U+FFFF
            > 	UNICODE:是国际组织制定的可以容纳世界上所有文字和符号的字符编码方案。目前的Unicode字符分为17组编排，0x0000 至 0x10FFFF，每组称为平面（Plane），而每平面拥有65536个码位，共1114112个。
            > 	UCS:通用字符集（Universal Character Set, UCS）是由ISO制定的ISO 10646（或称ISO/IEC 10646）标准所定义的标准字符集。UCS-2用两个字节编码，UCS-4用4个字节编码。
            > 	GBK:
            > 	ISO-8859:
            > 	BIG5:
            > 	CodeUnit:某种编码的基本组成单位就叫代码单元，比如UTF-8的代码单元为1个字节，UTF-16的代码单元为2个字节。
            > 	BOM:Byte Order Mark（字节顺序标记），（FE FF）标识字节序为高位优先（big-endian）。优先写入高8位。
            > 	
            >     -------------------------------------------------------------------------------
            >     
            >     JavaString保存的就是字符的Unicode码。它以前使用的是UCS-2编码方案来存储Unicode，后来发现BMP范围内的字符不够用了，但是出于内存消耗和兼容性的考虑，并没有升到UCS-4（即UTF-32，固定4字节编码），而是采用了上面所说的UTF-16，char类型可看作其代码单元。这个做法导致了一些麻烦，如果所有字符都在BMP范围内还没事，若有BMP外的字符，就不再是一个代码单元对应一个字符了，length方法返回的是代码单元的个数，而不是字符的个数，charAt方法返回的自然也是一个代码单元而不是一个字符，遍历起来也变得麻烦，虽然提供了一些新的操作方法，总归还是不方便，而且还不能随机访问。
            >     String.prototype.codePointAt():返回 一个 Unicode 编码点值的非负整数。返回值是在字符串中的给定索引的编码单元体现的数字，如果在索引处没找到元素则返回 undefined 。如果在指定的位置没有元素则返回 undefined 。如果在索引处开始没有UTF-16 代理对，将直接返回在那个索引处的编码单元。
            > Surrogate Pair是UTF-16中用于扩展字符而使用的编码方式，是一种采用四个字节(两个UTF-16编码)来表示一个字符，称作代理对
            >     String.prototype.charCodeAt():返回0到65535之间的整数，表示给定索引处的UTF-16代码单元 (在 Unicode 编码单元表示一个单一的 UTF-16 编码单元的情况下，UTF-16 编码单元匹配 Unicode 编码单元。但在——例如 Unicode 编码单元 > 0x10000 的这种——不能被一个 UTF-16 编码单元单独表示的情况下，只能匹配 Unicode 代理对的第一个编码单元) 。如果你想要整个代码点的值，使用 codePointAt()
            > */
            > ```
            >
            > [链接1](http://www.fmddlmyy.cn/text6.html)
            >
            > [链接2](https://www.jb51.net/article/130569.htm)
            >
            > [链接3]([https://xiaogd.net/%e9%9d%9e-bmp-%e5%ad%97%e7%ac%a6%e5%88%a4%e6%96%ad%e5%8f%8a%e5%88%a4%e6%96%ad%e5%ad%97%e7%ac%a6%e4%b8%b2%e4%b8%ad%e6%98%af%e5%90%a6%e5%8c%85%e5%90%ab%e9%9d%9e-bmp-%e5%ad%97%e7%ac%a6/#more-1315](https://xiaogd.net/非-bmp-字符判断及判断字符串中是否包含非-bmp-字符/#more-1315))
            >
            > [链接4]([https://xiaogd.net/%e5%ad%97%e7%ac%a6%e9%9b%86%e4%b8%8e%e7%bc%96%e7%a0%81%ef%bc%88%e4%ba%94%ef%bc%89-%e4%bb%a3%e7%a0%81%e5%8d%95%e5%85%83%e5%8f%8a-length-%e6%96%b9%e6%b3%95/#%E5%A2%9E%E8%A1%A5%E5%B9%B3%E9%9D%A2%E4%B8%AD%E7%9A%84%E5%AD%97%E7%AC%A6%E9%95%BF%E5%BA%A6](https://xiaogd.net/字符集与编码（五）-代码单元及-length-方法/#增补平面中的字符长度))