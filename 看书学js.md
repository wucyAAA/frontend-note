

#### const问题

for(const key in {a:1,b:2}){

​     console.log(key)      // a,b 

}

for(const value of [1,2,3,4,5]){

console.log(value)     //1,2,3,4,5

}

?? const值不是变了吗

#### 6种简单数据类型

number string boolean undefined null         symbol =>es6新增

undefined有null派生出的  布尔值都为假

#### 将其他类型的值转换为布尔值

let message = "hello world"

let messageAsBoolean = Boolean(message)



保罗•H•邓恩1.荣格自传 2.活出生命的意义 3.妈妈及生命的意义 4.爱的艺术 5.自卑与超越 6.恩宠与勇气 7.与生命相约 8.少有人走的路 9.个人形成论Overcoming Your Fear of Public Speaking: A Proven Method Motley, Michael T. Pearson (1997-08出版)   A Speakers Guidebook: Text and Reference Dan OHair 2008

#### 性能优化

v8在后台配置。让两个实例共享相同的隐藏类，因为这两个实例共享同一个构造函数和原型假设之后又添加了下面这行代码 a2.author='jake'。此时两个Article实例就会对应两个不同的隐藏类。根据这种操作的频率和隐藏类的大小，（delete删除属性也会，最佳实践是把不想要的属性设置为null）这又肯对性能产生明显影响，解决方案就是避免js的先创建再补充式的动态属性赋值，并在构造函数中一次性声明所有的属性，

#### 原始值包装类型

let s1 = 'xx'

let s2 = s1.substring(2)  

//自动创建的原始值包装对象则只存在于访问它的那行代码执行期间。

//这意味着不能再运行时给原始值添加属性和方法

s1.color = 'red'

console.log(s1.color)  //undefined

#### 字符串方法

1.concat()    2.slice() substring()     substr()  《第二个参数为截取几个字符》

3.indexOf()  lastindexOf()       4.startsWith() endsWith()   includes()     5.trim()   6.repeat()  复制字符串多少次

7.padStart()  padEnd()   将字符串填充到某长度的字符串可以指定以啥字符填充

8.toLowerCase() toUpperCase()  toLocaleLowerCase()    toLocaleUpperCase() 

9.match()  search()    10. replace() 第一个参数可以时字符串或正则 第二个参数可以是字符串或函数

11.***split()  传入一个参数，以这个参数为分隔符把字符串转换成数组***   12.localeCompare

#### for of 遍历字符串

```
for(const c of "abcde"){
  console.log(c)
//a
//b
....
}
```

#### 解构操作符解构字符串，把字符串分割为字符数组

```
let message =  "abcde"
console.log([...message]) //['a','b','c','d','e']
```

#### URL编码方法

encodeURL() encodeURLComponent()

#### eval()

用的少

#### window对象实现为global对象的代理

#### Math

Math.ceil()向上舍入最接近的整数    Math.floor() 向下舍入最接近的整数     Math.round()四舍五入  Math.fround()--         Math.abs()

#### Array

Array.from()   将类数组结构转换为数组实例   浅复制

- const a1=[1,2]
- const a2 = Array.from(a1)
- alert(a1===a2)   //false       **浅复制**

Array.of() 将一组参数转换为数组实例

Array.of(1,2,3,4)   //[1,2,3,4]     Array.of(undefined)   //[undefined]

数组length属性     可以删除数组的值

let a =[1,2,3]

a.length=2

cosole.log(a) // [1,2]

还可以添加值      a[a.legth] = 4

Array.isArray()  //确定一个值是否为数组

#### 数组实例方法        

检索数组内容的方法：keys() values() entries()   返回的是迭代器

```
const a =['foo','bar','baz']
for(const[id,ele] of a.entries()){
  alert(id,ele)
  //0 foo 
  ---
}
for of 吊
```

fill()填充数组            copywithin()   valueOf()

***将数组转换为字符串 toString()          join()可以传入一个参数作为分隔符***

push()       pop()                         类似栈  

shift() 删除数组第一项   unshift() 在数组开头添加任意多个值  返回新数组长度   类似队列

reverse()         sort()//可以传入比较函数

```javascript
function compare(value1,value2){
  return value1-value2            //比较函数
}
```

concat()  将两个参数与调用的数组拼成一个数组  两个参数可以是字符串

slice() //切割数组 返回被切割之后的数组 2参数          原数组不变

splice()  要删除第一个元素的位置    要删除元素的数量  要插入的元素/要替换的元素

splice()功能强大，删除 插入 替换！

严格相等：

​       indexOf() lastIndexOf() 返回下标      includes()返回布尔值        //查找数组中是否有某元素，有两个参数

断言函数：                            **|**    迭代方法:                                                                  归并方法： 2参数

​     findindex() find()             **|**           every()  filter()  forEach() map() some()              reduce()   reduceRight()  

```
const p=[
{
  name:'matt',
  age:27
},
{
 name:'Nicholas',
 age:29
}
]
alert(p.find((ele,index,array)=> ele.age<28))
=======================================================
let numbers =[1,2,3,4,5,4,3,2,1]
let everyResult = numbers.every((item,index,array)=>item >2) //false
let someResult = numbers.some((item,index,array)=>item >2) //true
let filterResult = numbers.filter((item,index,array)=>item >2) //[3,4,5,4,3]
let mapResult = numbers.map((item,index,array)=>item*2) // 对数组中每一项都乘2
==========================================================================
let values = [1,2,3,4,5]
values.reduce((prev,cur,index,array)=> prev +cur) //15
```

***map()方法非常适合创建一个与原始数组元素一 一对应的新数组***

#### Map

const m = new Map()

m.set()  m.get() m.has() m.size m.delete()

set() 方法返回映射实例，因此可以把多个操作连缀起来， m.set().set()---

可以把任何js数据类型作为key  entries() 方法能迭代map

#### WeakMap

只能把对象作为key值，。。。。。。（不能迭代好像，没看明白）

WeakMap实例不会妨碍垃圾回收，所以非常适合关联元数据 p665

set weakset --再见！

Array 所有定型数组 Map Set 都支持顺序迭代，都可以传入 for-of循环，这也意味着所有这些类型都兼容扩展操作符。扩展操作符在对而可迭代对象执行浅复制时特别有用，只需简单地语法就可以复制整个对象。

```javascript
 const a =[1,2,3,4]
 console.log([...a]);   //[1,2,3,4]
```

#### 浅复制意味着只会复制对象引用:

```javascript
let a =[{}]
let b = [...a]
a[0].name = 'zz'
console.log(b[0].name)
```

for循环文艺说法：技术循环

#### 震惊!!!数组也能解构

```
let arr = ['foo','bar','zz']
let [a,b,c] = arr
console.log(a,b,c)
```

#### 略：迭代器与生成器  

#### 另·

```
function myFun(a, b, ...manyMoreArgs) {
  console.log("a", a)
  console.log("b", b)
  console.log("manyMoreArgs", manyMoreArgs)
}

myFun("one", "two", "three", "four", "five", "six")

// a, "one"
// b, "two"
// manyMoreArgs, ["three", "four", "five", "six"] <-- notice it's an array
```

#### Object

给对象定义多个属性的方法 Object.defineProperties() 类似于 Object.defineProperty()

使用Object.getOwnPropertyDescriptor()方法可以取得指定属性的属性描述符 

类似于Object.getOwnPropertyDescriptors()。

Object.assign()方法用来合并对象，将每个源对象中可以枚举（Object.propertyIsEnumerable()）和自有（Object.hasOwnProperty()）属性复制到目标对象，可以有多个源对象。

Object.assign对一层对象是深拷贝，对多层是浅拷贝，如果赋值期间出错，则操作会终止并退出，同时抛出错误，它没有回滚之前赋值的概念，因此它是一个尽力而为，可能只会完成部分复制的方法。

#### 对象解构

```javascript
let p ={
	name:'wucy',
	age:20
}
let {name:pname,age:page} = p
console.log(pname,page);
```

#### 高！

解构在内部使用函数ToObject()把源数据结构转换为对象。这意味着在对象结构的上下文中，原始值会被当成对象。这也意味着null和undefined不能被解构，否则会抛出错误。

```javascript
let {length} = 'foobar'

console.log(length) //6

let {constructor:c} =4

console.log(c === Number) //true

let {_} =null //TypeError

let {_} =undefined //TypeError
```

解构并不要求变量必须在解构表达式中声明。不过，如果给事先声明的变量赋值，则赋值表达式必须包含在一对括号中： //不是很重要感觉

```
let pname
let p={
    name:'wucy'
};  要带分号
({name:pname}=p) //必须带括号 ，不用加let
console.log(pname);
```

解构如果出错，则整个解构赋值只会完成一部分。

#### 参数解构

```
let person ={
name:'wucy',
age:20
}
function printPerson(foo,{name,age},bar){
	console.log(arguments)
	console.log(name,age)
}
printPerson('1st',person,'2nd')
```

#### 构造函数

工厂模式虽然可以解决创建多个类似对象的问题，但没有解决对象标识的问题。

在实例化时，如果不想传参数，那么构造函数后面的括号可加可不加。

构造函数与普通函数唯一的区别就是调用的方式不同，任何函数只要使用new操作符调用就是构造函数。

#### 原型对象

```
Person(){}
let p1 =new person()
///////////////////
Person.prototype.__proto__ = {}  ==>Object.prototype
p1.__proto__ = Person.prototype={}
原型对象中包含constructor属性指向Person构造函数和后来添加的属性。
```

Object.getPrototypeOf()  :取得一个对象的原型

Object.setPrototypeOf() ：给一个对象设置新的原型对象

为了避免使用Object.setPrototypeOf(）可能造成的性能下降，可以通过Object.create()来创建一个新的对象，同时为它指定原型。 //**感觉挺奇怪的**--

hasOwnProperty()  可以区分该属性是否来自对象自身

#### in操作符

只要通过对象可以访问，in操作符就返回true //   'name' in person

for in  遍历对象和对象原型上的所有属性

Object.keys() 只遍历对象自身的属性

Object.getOwnPropertyNames() 只遍历对象自身的属性

Object.keys() ,Object.values() //返回对象值  Object.entries() //返回键/值对的数组    ==>数组也有这些同名方法

Object.keys() ,Object.values() ，Object.entries()属于浅复制

在前面的每个例子中，每次定义一个属性或方法都会把Person.prototype()重写一遍，为了减少代码冗余，直接通过一个包含所有的对象字面量来重写原型成为了一种常见的做法。

```
function Person(){}
Person.prototype={
	name:'zzz',
	age:20
}
```

但这样写之后，Person.prototype的constructor属性就不指向Person了。不能依靠constructor属性来识别类型

这样写constructor指向了Object。

#### 所以需要恢复constructor属性

```
Obeject.defineProperty(Person.Prototype,'constructor',{
	enumerable:false,
    value:Person
})             //惭愧写成setProperty。。。。。
```

**重写构造函数上的原型之后在创建的实例才会引用新的原型，而在此之前创建的实例任然会引用最初的原型。**

#### 原型链继承

关键代码：SubType.prototype = new SuperType()  把儿子的原型对象变成爸爸的实例对象

这也意味着一个问题  子类原型实际上变成了父类的实例，父类的实例属性，子类实例也可以用访问

第二个问题，子类型在实例化时不能给父类型的构造函数传参。

#### 盗用构造函数

为了解决原型包含引用值导致的继承问题，一种叫做的技术在开发社区流行起来，基本思路就是在子类构造函数中调用父类构造函数。

关键代码：SuperType.call(this,'参数')

问题：必须在构造函数中定义方法，因此函数不能重用，此外，子类不能访问父类原型上的方法。

组合继承

组合继承综合了原型链和盗用构造函数，将两者的优点集中起来。基本思路是使用原型链继承原型上的属性和方法，而通过盗用构造函数继承实例属性。

#### 原型式继承 

Object.create()   

后续略

#### 类

类就是一种特殊的函数 ，内部有constructor

类声明 class Person{}     类表达式 const Person = class{}

类可以像函数一样在任何地方定义，比如在数组中，也可以像其他对象或函数引用一样把类作为参数传递。

在类块中定义的所有内容都会定义在类的原型上

static  定义类方法 在类本身上

super

不要再调用super()之前引用this，否则会抛出referenceerror

super只能在派生类构造函数和静态方法中使用

super，要莫用它调用构造函数，要莫用它引用静态方法

抽象基类

new.target保存通过new关键字调用的类或函数，通过在实例化时检测new.target是不是抽象基类，可以阻止对抽象基类的实例化

关键代码:

```
class Vechicle{
constructor(){
if(new.target === Vechicle){
   throw new Error('Vehicle cannot be directly instantiated')
​               }
​          }
 }
```

#### 函数

箭头函数 

 let sum =(a,b) => return a+b 错误写法     不带大括号自动return，带了大括号要主动return

箭头函数和不能使用 arguments，super和new.target,也不能用作构造函数，也没有prototype属性

可以通过函数对象的name属性来获取函数名，如果函数是一个获取函数，设置函数，或者bind()实例化，那麽标识符前会加上一个前缀， bound foo  get foo  set foo

可以在函数内部访问arguments对象，从中取得传进来的每个参数值，arguments对象是一个伪数组对象，

```
function sayHi(name,message){
	console.log("hello"+name+','+message)
}
可以通过arguments[0]取得相同的参数值，因此，把函数重写成不声明参数也可以
function sayHi(){
	console.log("hello"+arguments[0]+','+arguments[1])
}
```

***在js中函数的参数只是为了方便才写出来的，并不是必须写出来的。***

#### 使用默认参数

function f1(name='wucy'){console.log(name)}

arguments始终以调用函数时传入的值为准。 默认参数可以是原始值或对象，或使用调用函数返回的值。

arguments还有一个属性callee，是一个指向arguments对象所在函数的指针。

箭头函数也可以使用默认参数。

#### ...扩展操作符

不能这么用：f1(...[1,2,3]) {--------------------}      晕了

收集参数，只能把它作为最后一个参数

```
function getSum(...a){
	return a.reduce((x,y)=>x+y,0)
}
getSum(1,2,3)         //会将参数收集成为一个Array实例
```

#### 函数声明与函数表达式

js引擎在任何代码执行之前，会先读取函数声明，并在上下文中生成函数定义。而函数表达式必须等到代码执行到它那一行，才会在执行上下文中生成函数定义。

```
//没问题！
console.log(f1())
function f1(){
	return '正确'
}
//错误！
console.log(f1())
let/var f1= function(){  //与let 和 var 无关
  return '错误'
}
```

函数对象上的一个属性：caller  这个属性引用的是调用当前函数的函数

```
function outer(){inner()}
function inner(){console.log(inner.caller)}
outer()
```

检测函数是否使用new调用的new.target

正常调用 new.target=undefined  new调用 new.target 将引用被调用的构造函数

函数对象还有length属性保存的是函数定义的命名参数的个数

call(this值，参数一，参数二)   这个第二个参数必须一个个列出来    

 apply(this值，[])     第二个参数也可以是argumens对象

bind(this值)

```
let color = 'yellow'
let o={
color:'red'
}
function f1(){
	console.log(this.color)
}
let f2 =f1.bind(o)
f2()
```

#### 闭包

作用域链

<img src="C:\Users\wuchuyao\Desktop\作用域链.jpg" alt="C:\Users\wuchuyao\Desktop\作用域链" style="zoom: 67%;" />

立即调用函数表达式

#### try/ catch

只要代码中包含了finally子句，try块或catch块中的return语句就会被忽略。

```
function testFinally(){
        try{
			return 1
        }catch{
        	return 2
        }finally{
        	return 3
        }

}

```

throw操作符，用于在任何时候抛出自定义错误。throw操作符必须有一个值，但值的类型不限。

throw newError(--)

#### json

json对象：{“name”:"wucy","age":22}       json数组：[22,"hi",true]

JSON.stringfy():将js序列化为JSON字符串

JSON.parse():以及将JSON解析为原生js值  都可以传参。

#### Ajax

默认情况下，HXR只能访问与发起请求的页面在同一个域内的资源

本人说：要请求的资源与发起请求的页面不在一个域内就发生了跨域。

跨域不是说ajax请求不能发送，而是得不到数据。

非同源受那些限制 （跨域）

cookie不能读取

DOM无法获得

Ajax请求不能获取数据

form表单不受同源策略限制。

#### jsonp跨域         json with padding

1.原理：利用了script标签发请求不受同源策略的限制，所以不会产生跨域问题

2.套路：动态构建script节点，利用节点的src属性，发出get请求，从而绕开ajax引擎 (要用stringfy方法)

3.弊端：只能解决get请求跨域的问题，后端工程师必须配合前端

4.备注：有这样一种感觉：前端定义函数，后端“调用”。

#### jquery解决跨域       

1.提前定义好一个等待被调用的函数

2.创建一个script节点 

3.为节点指定src地址，通知指定好回调函数的名称

4.讲解点插入页面

加个dataType：‘jsonp’ ===== 把上面4步全做了

#### cors解决跨域

res.setHeader('Access-Control-Allow-origin','http://localhost:63348')