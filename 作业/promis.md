## promie

是解决异步编程的一种解决方案，

解决了回调地狱

解决捕获能力

解决多个任务回调后导致多件顺序执行，性能消耗过多

### 概念：

promise 是个容器 里面包裹着异步操作的代码

语法上promise是一个对象，从它可以获取异步操作的消息

特点：

有3个状态  ：pending（进行中）fulfilled（已成功）rejected（已失败）

状态的变化只有两种情况

   1.从pending到fulfilled  从进行中到已成功

2. 从pending到rejected，从进行中到以失败

状态一旦固定 就不会改变

### 方法：

.then 成功的回调

then方法的返回结果是promise对象 ，对象状态的回调函数执行结果决定调用.then方法的返回结果是promise，

对象状态有回调函数的执行结果决定

.catch失败的回调

### 原理

底层是根据new  XMLHttpRequest()建立网络链接

all方法接受一个数组作为参数，如（p1,p2,p3）都是promise实例，如果不是，就会新调用下面讲到的promise.resolve方法，将参数转为promise实例，再进一步处理

语法：

promise.all(p1,p2,p3),then(res=>{console.log(res)})

特点：

接受的参数为数组

返回值为一个数组，进行获取最终的结果

只有参数全部返回成功的时候，才能返回数组，如果有一个参数返回失败，就直接返回失败

当一个参数返回失败的时候，全部返回失败