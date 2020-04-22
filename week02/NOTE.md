# 每周总结可以写在这里
预备知识：Unicode 字符集
• Blocks 编码组
• Basic Latin: 也即 ASCII 兼容部分
• 码点（Codeoints）: 0 - 127, String.fromCodePoint(97) --> "a"
• 16进制表示：U+0000 - U+007F ，即： 0x0000 - 0x007F,   String.fromCodePoint(0x0061) --> "a"
• 16进制字符串表示："\u0000" - "\u007F",  "\u0061" --> "a"
• 注意 String.fromCodePoint(i) 和 String.fromCharCode(i)  的区别：String.fromCharCode(i)  的 码点最大取值为  0xFFFF ， 超过了这个值就不能转换了，这时就要用 String.fromCodePoint(i) 了，另外 String.fromCodePoint(i) 可以传入多个参数 ：
String.fromCodePoint(0x1f601,0x1f601,0x1f601)
"😁😁😁"
• 特例要记住的字符： LF： U+000A,  SPACE: U+0020
• CJK Unified Ideographs : 中日韩文，U+4E00 ~ U+9FFF
• 有一些增补区域，不上上述范围
• BMP 基本字符 : U+0000 - U+FFFF
• \u 转义
• 实际上是可以使用中文作为变量名的，这个时候最好就是用  \u 进行转义，而不是直接用 中文名做变量，因为涉及文件的编码保存方式等，实际工作中，也最好都有 ASCII 码 中的字符
• Categories
• space 空格系列
var 厉害 = 1
console.log(厉害)   // 1
'厉害'.codePointAt(0).toString(16)   // "5389"
'厉害'.codePointAt(1).toString(16)   // "5bb3"
var \u5389\u5bb3 = 2
console.log(厉害)   // 2
// 也可以用 charCodeAt 方法
'厉'.charCodeAt().toString(16)   // "5389"
<script>
for(let i = 0; i < 128; i++) {
  console.log(String.fromCodePoint(i), i)
  console.log(String.fromCharCode(i), i)
  document.write("<span style='background-color: lightgreen;'>" + String.fromCodePoint(i) + "</span><br/>")
}
</script>  
参考
• 字符集：字符编码（英语：Character encoding）、字集码是把字符集中的字符编码为指定集合中某一对象（例如：比特模式、自然数序列、8 位组或者电脉冲），以便文本在计算机中存储和通过通信网络的传递。常见的例子包括将拉丁字母表编码成摩斯电码和 ASCII。其中，ASCII 将字母、数字和其它符号编号，并用 7 比特的二进制来表示这个整数。通常会额外使用一个扩充的比特，以便于以 1 个字节的方式存储。在计算机技术发展的早期，如 ASCII（1963 年）和 EBCDIC（1964 年）这样的字符集逐渐成为标准。但这些字符集的局限很快就变得明显，于是人们开发了许多方法来扩展它们。对于支持包括东亚 CJK 字符家族在内的写作系统的要求能支持更大量的字符，并且需要一种系统而不是临时的方法实现这些字符的编码。
• Unicode ：中文：万国码、国际码、统一码、单一码。是计算机科学领域里的一项业界标准。它对世界上大部分的文字系统进行了整理、编码，使得电脑可以用更为简单的方式来呈现和处理文字。
• ASCII ：（American Standard Code for Information Interchange，美国信息交换标准代码）是基于拉丁字母的一套电脑编码系统。它主要用于显示现代英语，而其扩展版本延伸美国标准信息交换码则可以部分支持其他西欧语言，并等同于国际标准 ISO/IEC 646。美国信息交换标准代码是这套编码系统的传统命名，互联网号码分配局现在更倾向于使用它的新名字 US-ASCII[2]。美国信息交换标准代码是美国电气和电子工程师协会里程碑之一。
Atom 
• Grammar
• InputElement
• Runtimes
• Types
InputElement
• WhiteSpace
• <TAB>: TAB 制表符（打印机时代，制表时隔开字符很方便）
• <VT> ：纵向制表符
• <FF> ：Form Feed
• <SP> :  SPACE
• <NBSP> :  NO-BREAK-SPACE 不换行空格
• <ZWNBSP> : ZERO WIDTH NO BREAK SPACE  零宽空格
• <USP> : Unicode space 空格系列
• LineTerminator
• <LF> : LINE FEED, 也即 \n ，开发中保持用这个
• <CR> :  回车 \r
• <LS> : 下面这两个不用
• <PS>
• Comment
• //  单行注释
• /*  */  多行注释
• Token : 记号、标记。JS 里有效的输入元素都可以叫 Token。
• Punctuator ：符号
• IdentifierName
• Identifier : 标识符
• 变量名
• 属性
• Keywords : 关键字
• Future Reverse Word： enum
• Literal : 字面量
• Number
• IEEE 754 Double Float
• grammar
• DecimalLiteral : 十进制数
• 0
• 0.
• .0
• 1.2e10
• BinaryIntegerLiteral ： 二进制数  0b010  --> 2
• OctalIntegerLiteral ： 八进制数   0o010   --> 8
• HexIntegerLiteral ： 十六进制数  0x010   --> 16
• 最佳实践
• Safe Integer: 安全整数范围， Number.MAX_SAFE_INTEGER.toString(16)  --> "1fffffffffffff"
• Fload Compare: 浮点数比较，浮点数比较时，需要加精度, Math.abs(01 + 0.2 -03) <= Number.EPSILON
• String
• Character 字符
• ASCII
• Unicode
• UCS: U+0000 - u+FFFF
• ISO-8859
• BIG5
• GB: 
• GB23122
• GBK(GB13000)
• GB18030
• Code Point 码点
• Encoding : 编码方式
• UTF8
• UTF16
• grammar
• "DoubleStringCharacters" ： 双引号 "abc"
• 'SingleStringCharacters' ： 单引号 'abc'
• `Template` 模板字符串 `abc`
• Boolean
• true
• false
• Null
• Undefined 
参考：
• NBSP ：不换行空格（英语：no-break space，NBSP）是空格字符，用途是禁止自动换行。HTML 页面显示时会自动合并多个连续的空白字符（whitespace character），但该字符是禁止合并的，因此该字符也称作“硬空格”（hard space、fixed space）。Unicode 码点为：U+00A0 no-break space。
• 零宽空格：（zero-width space, ZWSP）是一种不可打印的 Unicode 字符，用于可能需要换行处。在 HTML 页面中，零宽空格可以替代。但是在一些网页浏览器（例如 Internet Explorer 的版本 6 或以下）不支持零宽空格的功能。
• JavaScript 浮点数陷阱及解法
• 揭秘 0.1 + 0.2 != 0.3
• 程序员趣味读物：谈谈Unicode编码
• 正则表达式
Types
• Number
• String
• Boolean
• Null
• Undefined
• Objject
• Symbol