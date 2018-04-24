#### go内置关键词（25个均为小写）`

| break    | default     | func   | interface | select |
| -------- | ----------- | ------ | --------- | ------ |
| case     | defer       | go     | map       | struct |
| chan     | else        | goto   | package   | switch |
| const    | fallthrough | if     | rage      | type   |
| continue | for         | import | return    | var    |

#### `go的注释方法`

```bash
// #单行注释
/* */ #多行注释
```

`杂七杂八`

```bash
package main
#当前程序包名
import "fmt"
import (
		"fmt"
		"os"
	)
#导入包，go下如果导入不需要的包执行会报错

const PI = 3.14
#常量，常量设置后运行程序的时候会被编译进去无法修改的值

var  name = "yyc"
#全局变量

type  newtype int
#一般类型声明

type  abc struct{}
#结构声明

type  abc interface{}
#接口声明
```

####`使用别名来导入包`

```bash
package main
import  yyc "fmt"
func main(){
    yyc.Println("OK")
}
#给fmt包设置了一个yyc的别名，在使用的时候为yyc即可
```

#### `go的数据类型`

```bash
布尔值：bool
    长度：1字节
    取值范围：true , false
    注意事项：不可用数字代表true或false

    整型：int/uint
    根据运行平台可能为32或64位

    8位整型：int8/uint8
    长度：1字节
    取值范围：-128~127/0~255
    字节型：byte(uint8别名)

    16位整型：int16/uint16
    长度：2字节
    取值方位：-32768~32767/0~65535

    32位整型：int64/uint64
    长度：8字节
    取值范围：-2^64/2~2^64/2-1/0~2^64-1

    浮点型:float32/float64
    长度：4/8字节
    小数位：精确到7/15小数位


    复数：complex64/complex128
    长度:8/16字节
    足够保存指针的32位或64位整数型:uintptr

    其他值类型
    array、strict、string

    引用类型
    slice、map、chan

    接口类型：inteface
    函数类型：func
    
    类型零值
    零值并不等于空值，而是当变量被声明为某种类型后的默认值，通常情况下值类型的默认值为0，bool为false，string为空字符串
    
       声明类型别名
    type  （
        byte  int8
        rune  in32
        ByteSize int64
  	  ）
```

#### `单个变量的声明与赋值`

```bash
全局变量的声明可使用var()的方式进行简写
全局变量的声明不可以省略var，但可使用并行方式
所有变量都可以使用类型推断
局部变量不可以使用var()的方式简写，只能使用并行方式
如：
var  a,b,c,d int 
a,b,c,d  = 1,2,3,4
var a,b,c,d int = 1,2,3,4
a,_,c,d= 1,2,3,4
//_表示跳过2
```

#### `变量的类型转换`

```bash
GO中不存在隐式转换，所有类型转换必须声明
转换只能发生在两种相互兼容的类型之间
类型转换的格式：
<ValueA> [:] = <TypeOfValueA>(<ValueB>)
var a float32 = 100.1
b := int(a)
#b的值为Int类型的数字，值为100

将Int类型转换成string字符串类型，直接转的话会把数字转换成对应的ascii表的值
如：
var a = 64
b :=string(a)
#b的值为ascii表中的数字64，对应的值为@

强制把int类型数字转换成字符串类型
import "strconv"
#需要导入上面的模块

var a = 1
b :=strconv.Itoa(a)
#这样b的值就是字符串类型的1

把字符串类型的数字强制转换成int类型的值
也需要导入上面的模块
import "strconv"
var a string = "12"
b,_ = strconv.Atoi(a)
#把字符串类型的12数字转换成int类型的数值
```

#### `常量的定义`

```bash
常量的值在编译时就已经确定
常量的定义格式与变量基本相同
等号右侧必须是常量或者常量的表达式
常量表达式中的函数必须是内置函数

常量的声明(常量的值设置后，当程序编译后就无法修改)：
const a int =1 
#声明一个名为a的常量，值为1

常量的几种声明：
const a int = 1
#声明一个名称为a的Int类型的常量
count  b = 'A'
#声明一个名称为b的string类型的常量
const (
		c = a
		d = a+1
		e = a +2
	)
#声明多个常量
const a,b,c = 1,'2','3'
const(
	d,e,f = 1,2,3
)
#声明多个常量并赋值

 const (
         a =  1
          b
          c 
          a ,b = 1,'w'
          c,d 
)
#上面的b和c都会继承a的值，顺序是b继承a，c继承b,第二组c继承a，d继承b


常量的初始化规矩与枚举
在定义常量组时，如果不提供初始值，则表示将使用上行的表达式
使用相同的表达式不代表具有相同的值
Iota是常量的计数器，从0开始，组中每定义1个常量自动递增1
通过初始化规则与iota可以达到枚举的效果
每遇到一个const关键字，iota就会重置为0
如：
func main() {
	const (
		a = iota
		b
		c
	)
	#c的值为2，iota的值为0开始，当一组里面有多个常量，并且后面的常量都没赋值时，iota的值从0到一共有多少个常量的数量为值，上面的有3个常量，iota从0开始，所有最终c的值为2
	const (
		d = iota
		e
		f
		g
		h
	)
	fmt.Println(h)
	#当出现多个const的关键词时，最下面的const关键词的iota的值就会重置为0
```

#### `运算符`

```bash
GO中的运算符均是从左至右结合
优先级(从高到底)
^ 		! 	(一元运算符)	
*	/	%	<<	>> 	&	&^
+	-	|	^
			(二元运算符)
==	!=	<=	<=	>=	>
<-			(专门用于channel)
&&	#必须全部满足才执行后面的语句
||	#满足一个条件就执行后面的遇见

如：
            a := 10
            if a > 5 && (a/5) > 3 {
            #&&：必须满足2个条件才执行打印ok        
            if a >5 || (a/5) > 3
            #满足其中一个条件就打印OK
                fmt.Println("OK")
            }
-----------------------------------------------

  		 /*
            6  :  0110
            11 : 1011
            --------
            &  0010 = 2
            |  1111 = 15
            ^  1101 = 13
            &^ 0100 = 4
            #&^:从11的1011跟6的0110比，从下往上，都是二进制

            */
            
            
            

```

