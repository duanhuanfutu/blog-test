## 一、JS对象

object 对象 唯一一种复杂类型

定义：

1. 无序的数据组合
2. 键值对的集合

写法1
 ~~~~
let obj = { 'name' : 'frank', 'age' = 18}
~~~~
写法2
~~~~
let obg = new object ( { 'name' : 'frank'} )
~~~~
写法3
~~~~
console.log ( { 'name' : 'frank'})
~~~~

'属性名' : ' 属性值'

细节
1. 键名是字符串，不是标识符，可以包含任意字符
2. 引号可以省略，省略之后只能写标识符
3. 就算省略了引号，键名也还是字符串

Object.keys(obj) 可以得到所有的 key

如果想用一个变量名做属性名，那就用 [ ] 括起来


## 二、 对象的隐藏属性

1. JS中每一个对象都有一个隐藏属性
2. 这个隐藏属性储存着其共有属性组成的对象的地址
3. 这个共有属性组成的对象那个叫做原型
4. 也就是说隐藏属性储存这原型的地址

除了字符串，symbol也可以用作属性名，但是现在用不着
~~~~
let a = symbol ()
let obj = { [a] : 'hello'}
~~~~

## 三、属性删除

示例
~~~~
obj.xxx = undefined
delete obj.xxx
~~~~
两者的区别：
1. delete 会删除属性名和属性值，就像删除一整个文档
2. undefined 只能删除属性值，类似只删除文档的内容，但是文档还在。

~~~~
delete obj.xxx 或者 delete obj[ 'xxx']
~~~~
就可以删除 obj 的属性

判断是否删除成功
~~~~
'xxx' in obj ===false
~~~~
就是删除成功了

但是
~~~~
obj.xxx === undefined 
~~~~
不能判断 'xxx' 是否为 obj 的属性

## 四、读属性

怎么查看自身所有的属性
~~~~
Object.keys(obj) 属性名
Object.values(obj) 属性值
~~~~
怎么查看共有属性
~~~~
①   console.dir(xxx)
②   xxx.__proto__  这种不推荐
~~~~

怎么分辨一个属性是自身的还是共有的
~~~~
xxx.hasOwnProperty( ' ' ) // true 就是是自身的属性
                         //false 就是共有属性 
~~~~

xxx.hasOwnProperty( ' ' ) 和 'xxx' in obj 之间的区别
前者可以判断一个属性是否是自身的属性 
但是后者只可以判断你是否拥有这个属性
## 五、原型
1. 每个对象都有原型
2. 原型里存着对象的共有属性
3. 比如 obj 的原型就是一个对象
4. obj._ _proto_ _存着这个对象的根

对象的原型对象

1. obj = { } 的原型，就是所有对象的原型
2. 这个原型包含所有对象的共有属性，是对象的根
3. 这个原型也有原型，内容是 null

怎么读单个属性的值
1. 点语法 
~~~~
obj.属性名
~~~~
2. 中括号语法
~~~~
obj[ ' 属性名‘]   优先使用这一种
~~~~

## 六、修改或增加属性

   直接赋值
   ~~~~
   1. let obj = {name:'frank'}
   2. obj.name='frank'
   3. obj['name']='frank'
   4. obj['na'+'me']='frank'
   5. let key = 'name';obj[key]='frank'
   ~~~~

批量赋值
~~~~
object.assgin (obj,[属性名:'属性值',属性名:'属性值'])
~~~~
一般不要修改或增加共有属性，如果偏要修改
~~~~
obj.__proto__.toString='xxx' 不推荐
Object.portotype.toString='xxx'
~~~~
修改隐藏属性，不推荐使用  __proto_ _
示例
~~~~
let obj = {name :'frank'}
let obj2 = {name:'jack'}
let common = {kind:'human'}
obj.__proto__ = common
obj2.__proto__ = common
~~~~
推荐使用
~~~~
let obj = Object.create(common)
obj.name='frank'
let obj2 = Object.create(common)
obj2.name = 'jack'
~~~~
