---
title: "Swift基础语法"
layout: page
data: 2016-06-11 00:00:00
---

#变量和常量#

	// 不用写分号
	// 一般首选 let
	// 变量
	var num1 = 10

	// 常量
	let dou1 = 10.8

	// 计算必须类型相同，没有隐式转换
	var sum = Double(num1) + dou1

#逻辑判断#

##if##

	// 逻辑判断 ---- if  1.没有（）2.必须有{} 3.只有 true/false（没有非零即空）
	if num1 >= 10 {
    	print("大于等于10")
	}

##三目运算##

	// 三目
	let c = Double(num1) < dou1 ? 10 : dou1

##switch##

	/**
    1. 值可以是任何类型
    2. 作用域，仅在 case 内部有效
    3. 不需要 break
    4. 每一个 case 都需要有代码
 	*/

	let name = "小胡"
	switch name {
    	case "老王":
        	let age = 80
        	print(age)
    	case "老了", "理发":
        	print("pengyou")
    	default:
        	print("out")
	}

##循环##
	
	// 0~9
	for i in 0 ..< 10 {
	    print(i)
	}
	// 0~10
	for i in 0 ... 10 {
	    print(i)
	}

	// Range<Int> 范围
	let range = 0..<10

##数组##

	// 使用‘[]’ 创建数组
	// [String] 表示存放字符串的数组
	let array = ["重视","好"]

	// Swift中可以直接存放数字，不需要包装
	// 如果数组中存在的数据类型不一致，自动推导的格式是【NSObject】
	let arr1 = ["huhuhu", 67, array]

	// 遍历数组
	for name in array {
	    print(name)
	}

	// 可变数组 var & 不可变数组  let

	// 数组添加
	var arr2 = array;
	arr2.append("效果")
	// 删除
	let strii = arr2.removeFirst()
	print(arr2)

	// 数组容量
	print(arr2.capacity)

	arr2.removeAll(keepCapacity: true)


	// 添加数据 ---- 追加元素  ----- 跟踪变化
	var arr3 = [String]()
	for i in 0..<10 {
	    arr3.append("\(i)")
	    print("索引：\(i)  数组容量：\(arr3.capacity)")
	}

	// 跟踪发现，如果数组容量不足，在原来的基础上 X2

	var arryM1: [String]  // 声明一个装字符串的数组，没有实例化
	var arryM2 = [String]() // 实例化

	// 创建数组，并指定容量
	//var arryM = [Int](count:5 repeatValue:0)-- 好像语法变了

	// 数组拼接  注意数组中的类型必须相同
	var arry1 = [1,2,3,4]
	var arry2 = [5,6,7,8]

	arry1 += arry2

##字典##

	// 定义字典 也是 [String: NSObject] [key: value]
	// key 同常是字符串  value可以是任意类型
	var dict = ["name": "傅饶", "age": 23]

	// let 不可变 & var 可变
	// 给字典赋值，直接用["key"] = value
	dict["height"] = 1.78
	dict

	// 给字典设置数值的时候，如果 key 存在，值会被修改
	dict["name"] = "小组"
	dict

	// 字典遍历
	// k, v 是随便写，前面是 key ,后面是 value
	for (k, v) in dict {
	    print("ley:\(k)   value:\(v)")
	}

	// 合并
	let dict2 = ["title": "老板", "name": "老王"]

	// 遍历dict2
	for (k, v) in dict2 {
	    dict[k] = v;
	}

##函数##

	// 定义个函数
	// 格式： func 函数名（形式参数列表）-> 返回类型 {// 代码实现}
	func sum(x: Int, y: Int) -> Int {
	    return x + y
	}

	// 函数调用 函数名（值1，参数名：值2）
	sum(10, y: 22)

	// 外部参数 num1 ,num2 是供外部调用的程序员参考的，是保证函数的语义更加清晰
	// 内部参数 x,y 数据函数内部使用
	func sum1 (num1 x: Int, num2 y: Int) -> Int {
	    return x + y
	}
	sum1(num1: 18, num2: 88)

	// 没有返回值，有三种写法
	// 1.直接省略
	func demo1 () {
	    print("hehe")
	}
	// 2.-> Void
	func demo2 () -> Void {
	    print("haha")
	}
	// 3.-> ()
	func demo3 () -> () {
	    print("xixi")
	}

##闭包##

	// 可以暂时理解成 OC 中的 Block
	/*
	    1. 预先准备好代码
	    2.可以作为参数传递
	    3.在需要的时候执行
	 */


	// 定义个函数
	func sum (num1 x: Int, num2 y: Int) -> Int {
	    return x + y
	}

	let demoFunc = sum
	demoFunc(num1: 1, num2: 3)

	// 闭包定义
	/*  
	    1. 行参，返回值，代码都包含在{}中
	 */

	// 最简单的闭包 ，如果没有参数/返回值 统统（包括 in）都可以省略
	let funcDemo1 = {
	    print("我是最简单的闭包")
	}
	// 执行闭包
	funcDemo1()

	// in 就是区分函数定义和代码实现的
	// 格式：{（带外部参数的形参列表）-> 返回值 in 代码实现}
	let funcDemo2 = { (x: Int, y: Int) -> Int in
	    return x + y
	}

##String##

	/**
	    String 结构体，效率高，一般采用String
	    NString 继承NSObject
	 */
	var str = "Hello, playground"

	// String 支持遍历
	for c in str.characters {
	    print(c)
	}

	// 字符串拼接
	let name: String? = "xiaohong"
	let age = 10
	let title = "你是我的"
	let rect = CGRect(x: 0, y: 0, width: 100, height: 100)

	print(name ?? "" + String(age) + title)

	// \(变量名) 就会自动转换拼接
	// 如果是可选的转换，会带上 ‘Optional' ,提示开发人员，只是可选的
	// 拼接字符串有一个小陷阱 ？(界面问题，会带上Optional)
	print("\(name) \(age) \(title) \(rect)")

	let h = 7;
	let m = 8;
	let s = 4;
	print("\(h):\(m):\(s)")

	let str1 = String(format: "%02d:%02d:%02d", arguments: [h,m,s])

	//Range 在Swift变迁中变化非常大
	// 截取字符串 Swift遇到Range 最好把String 转成 NSString 
	(str as NSString).substringWithRange(NSMakeRange(2, 4))
	// "rrrrr".endIndex 表示"rrrrr"的最后一个索引
	str.substringFromIndex("rrrrr".endIndex)