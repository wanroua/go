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
```

