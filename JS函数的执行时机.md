### JS 函数的调用时机

1. 解释为什么如下代码会打印出6个6
~~~~
let i =0
for( i=0; i<6 ; i++ ){
    setTimeout(（）=>{
        console.log(i)
    }，0 )
}
~~~~

setTimeout 会先执行完 for 循环，然后在打印出 i，等 i = 6 的时候就会退出 for 循环，所以就会打出6个6。


2. 写出让上面代码打印0，1，2，3，4，5的方法

用for let 可以达到打印出0，1，2，3，4，5 的效果
~~~~
for （let i =0 ; i<6 ; i++){
    setTimeout(()=>{
        console.log(i)
    },0)
}
~~~~
