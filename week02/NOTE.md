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
    * InputElement
      * whitespace
      * LineTerminal
      * Comment
      * Token
        * 