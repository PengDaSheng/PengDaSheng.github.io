# Swift 基础语法
##学习资料
- 猫神的书

	- [100个SwiftTips--OneCat](media/14575891072141/Swifter.epub)
	- [Swifte](media/14575891072141/Swifter.pdf)

- 苹果官方资料
	- [Github源代码] (https://github.com/apple/swift)
	- [官网]( https://swift.org/)
	- [中文版本] (https://github.com/numbbbbb/the-swift-programming-language-in-chinese/wiki)

## 基础语法
### 初体验
```swift
import UIKit

/*Code written at global scope is used as the entry point for the program, so you don’t need a main() function.*/
var str = "Hello, playground"
str = " i can change"

/** 语句中可以不加分号 */
var number : Int = 10
let alpha : Double = 20.0
let a = 30
number = 20

/** 打印 */
print(str)
```

###常量和变量
- 1. 开发中常量优先，需要在修改为`var`
- 2. 常量对象不可改变,但是可以拿到常量对象修改该常量对象的内部属性

###创建对象
```SWIFT
//创建对象
var view:UIView  = UIView()
view = UIView()

/** ****************03-创建对象****************** */

let viewA : UIView = UIView(frame: CGRect(x: 0, y: 0, width: 100, height: 100))

viewA.backgroundColor = UIColor.blueColor()
- 使用枚举方法1
let button : UIButton = UIButton(type: UIButtonType.ContactAdd)
- 使用枚举方法2
//let button : UIButton = UIButton(type: .Custom)

button.center = CGPoint(x : 50, y :50)
viewA.addSubview(button)
```

### 数据类型

- 1,强类型语言,任何标识符的==类型必须明确.==无id类型;
- 2,类型推导;(option + 左键)查看具体类型

	```swift
	var b = 30
	//b = 3.14(打开会报错)
	var c = 3.1415
	``` 

### 基本运算
- 1. 必须保证类型一致才能计算.==swift不包含隐式准换==

```swift
let m = 23
let n = 90.9
let result = Double (m) + n
```
### 逻辑分支
#### if
- 1,不再是非0 即1了,必须有明确的Bool值(flase 和 true) ; 
- 2,省略()

```swift
let k = 10
if k > 10 {
    print("真的")
}else{
    print("假的")
}
----- else if------

let score = 88

if score > 100 || score < 60{
    print("分数无意义")
}else if score > 90{
    print("优秀")
}else if score > 80{
    print("良好")
}
```

#### 三目运算符
```swift
let k1 = 90
let k2 = 50

var resultA = k1 > k2 ? k1 : k2
```

#### guard(守卫者)
- 1. guard必须写在函数中
- 2. 函数示例

```swift
let age = 20

func online(age: Int){
    if age > 18{
        print("可以")
    }else{
        print("不可以")
    }
}
online(age)
```

- 3.guard(卫士)举例

	- 如果条件成立,会执行后面的代码块
	- 如果不成立,就会执行大括号里面的,大括号里面必须要跟上break,continue,return等
	
		```swift
		func onlineB(age:Int,money:Int){
		    //如果条件成立,会执行后面的代码块
		    //如果不成立,就会执行大括号里面的,大括号里面必须要跟上break,continue,return等
		    guard age >= 18 else{
		        return
		    }
		    
		    guard money >= 100 else{
		        return
		    }
		    print("可以上网")
		}
		
		onlineB(20, money: 100)
		```

#### switch

- 1,可以不要括号,不要break,  『系统默认添加』   
- 2,case穿透关键字`fallthrough`

```swift
let sex = 0;

switch sex {
case 0:
    print("男")
    fallthrough
case 1:
    print("女")
default:
    print("其他")
}
```

- 3,case 后面可以跟多个条件

	```swift
	switch sex {
case 0, 1:
    print("正常人")
default:
    print("其他")
}
	```
- 4,判断浮点类型

	```swift
	let k3 = 3.14
	switch k3{
	case 3.14:
	    print("π")
	default:
	    print("NO π")
	}
	```
	
- 5,判断字符串

	```swift
	let k5 = 20
	let k6 = 30
	
	let operation = "-"
	var res = 0;
	
	switch operation{
	case "+":
	    res = k5 + k6
	case "-":
	    res = k5 - k6
	case "*":
	    res = k5 * k6
	case "/":
	    res = k5 / k6
	default:
	    print("错误字符")
	}

	```
	
- 6,判断区间

	```swift
	let points = 98
	switch points{
	case 0..<60:
	    print("不及格")
	case 60..<80:
	    print("及格")
	case 80..<90:
	    print("良好")
	case 90...(100):
	    print("优秀")
	default:
	    print("不是一个分数")
	}
	```

#### 循环

```swift
/** ********for循环******** */
//1,普通的
for var k5 = 0; k5 < 10;k5++ {
    print(k5)
}

//2,for in 遍历区间
for k6 in 0..<10{
    print(k6)
}

//3,for in 不需要用到下标的情况,用_表示
for _ in 0...9{
    print("Hello World")
}

/** ********while /do while循环,了解******** */
/** ********while循环******** */
//1,没有非0即1;
var aa = 10

while aa > 0{
 aa--
    print(aa)
}

/** ********while循环******** */
var bb = 0
repeat{
    bb++
    print(bb)
}while (bb < 10)
```

## 数据类型
### 字符串类型(String)

- 简介
	- 字符串在任何的开发中使用都是非常频繁的
	- Objc和Swift中字符串的区别
		- 在Objc中字符串类型时NSString,在Swift中字符串类型是String
		- Objc中字符串@"",Swift中字符串""
- 使用 String 的原因
	- String 是一个结构体，性能更高
	- NSString 是一个 Objc 对象，性能略差
	- String 支持直接遍历
	- Swift 提供了 `String` 和 `NSString` 之间的无缝转换(`String as NSString`)

- 常见用法

```swift
- 1. 字符串的定义

let string = "Hello,pengsheng"

- 2. 字符串的遍历

for charactor in string.characters
{
    print(charactor)
}
- 3. 字符串和字符串的拼接

let sta = "大圣"
let stb = "我爱你"
let ds = sta + stb

- 3. 字符串和其他数据类型的拼接

let agg = 18
let name = "大圣"
let height = 188
let info = "my name is \(name) ,age is \(agg),height\(188)"

let min = 3
let second = 14
let times = "0\(min):0\(second)"
let timesTR = String(format:"%02d:%02d", arguments: [min,second])

- 4. 字符串的截取

let str5 = "www.520it.com"
//转换时因为参数更好设置,创建Index没有直接使用int简单,创建NSRange比Range更好创建
//str5.substringWithRange(<#T##aRange: Range<Index>##Range<Index>#>)
//str5.substringToIndex(<#T##index: Index##Index#>)
let header = (str5 as NSString).substringToIndex(3)
let midle = (str5 as NSString).substringWithRange(NSRange(location: 4, length: 5))
let footer = (str5 as NSString).substringWithRange(NSRange(location: 10, length: 3))
```

### 数组类型(Array)
- 简介
	-	数组（`Array`）是一串有序的由相同类型元素构成的集合
	- 数组中的集合元素是有序的，可以重复出现
	- Swift中的数组
		- swift数组类型是Array，是一个『泛型集合』 
- 常规使用
![](media/14575891072141/14576063822611.jpg)
![](media/14575891072141/14576064945852.jpg)
![](media/14575891072141/14576065915421.jpg)

### 字典(Dictionary)类型
- 常见用法

![](media/14575891072141/14576067981955.jpg)

![](media/14575891072141/14576071230588.jpg)

### 元组(Tuples)类型
![](media/14575891072141/14576072738768.jpg)

###可选类型(Optinals)
- swift是强制类型语言,要求所有的变量或者常量在初始化的时候必须制定类型;
- 因为==nil类型==在swift中也是一种数据类型.所以不能随意赋值给其他参数
- 引出可选类型

- 基本使用
	- 封包
![](media/14575891072141/14576077305592.jpg)
	- 解包
![](media/14575891072141/14576078683723.jpg)

![](media/14575891072141/14576080143547.jpg)

### 函数『func』 类型

- 基本使用

![](media/14575891072141/14576082105394.jpg)

- 函数注意事项

![](media/14575891072141/14576086139062.jpg)

## 类和对象
###swift中的类
- 基本知识

![](media/14575891072141/14576089254959.jpg)

## 额外注意点
![](media/14575891072141/14576089937250.jpg)

## 补充与注意事项
### 格式问题
- 空格很重要

```swift
let com = m > n ? m : n//注意空格很重要,特别是❔和！的
``` 

- 记得这种拼接字符串的格式

```swift
let minite = 3;
let second = 5;
let time = String(format: "%02d:%02d", minite,second)//记得这种格式
```

- 截取字符串别越界

```swift
let url = "www.520ps.com"
let header = (url as NSString).substringToIndex(3)
let middler = (url as NSString).substringWithRange(NSRange(location: 4, length: 5))//注意别越界访问
let footer = (url as NSString).substringWithRange(NSMakeRange(10, 3))
```
- 给可变数组添加元素只能用**.append()**

```swift
var arrM = [String]()//注意,追加必须使用append,不能用arrM[0] = 1;这样是改
arrM.append("one")
arrM.append("two")
arrM.append("three")
arrM
```

- 遍历数组的简单方法的本质

```swift
for a in arrM{//本质是搞一个参数去接收遍历出来的值.直接取出数组元素,
//而不是脚标
    print(a)
}
``` 
- 两个数组相加得到的是可变的数组还是不可变的数组?

```swift
var newArr = arrM + arrZ
/*可变数组和不可变数组相加得到的值是否可变取决于用什么类型去接收,NB*/
newArr[0] = "2"
```

- 字典的遍历在swift中不要用小括号哦

```swift
let dictX = ["tel":"10086","addrres":"Mars"]
for(key,value) in dictX{
    dictM[key] = value//注意:是[]而不是()
}
```

- 给可选类型解包有哪些安全的方法?

```swift
let urlStr = "www.520ps.com"

let urll = NSURL(string: urlStr)

if urll != nil{
    let request = NSURLRequest(URL: urll!)//强制解包
}

if let urlM = urll{
    let request = NSURLRequest(URL: urlM)
}
//系统底层会做判断: 1,如果可选类型为空,那么就什么都不干;2,如果不为空就会把可选类型解包出来,赋值给恰年的那个量,并执行大括号里面的代码;
if let urlN = NSURL(string: urlStr){//给系统判断解包
    let res = NSURLRequest(URL: urlN)
}
```





###  `guard`强调
- guard是Swift2.0新增的语法
- 它与if语句非常类似，它设计的目的是提高程序的可读性
	- **使用guard也可以用于可选绑定** 
- guard语句**==必须带有else语句==**，它的语法如下：
	- 当条件表达式为true时候跳过else语句中的内容，执行语句组内容
	- 条件表达式为false时候执行else语句中的内容，跳转语句一般是return、break、continue和throw

- guard **==只能用在函数内部==**,不能单独使用;


	
	




