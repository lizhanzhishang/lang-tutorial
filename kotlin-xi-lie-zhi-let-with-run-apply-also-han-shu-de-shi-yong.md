# Kotlin 系列之let、with、run、apply、also函数的使用

源码位于：Standard.kt中

参考网址：[https://blog.csdn.net/u013064109/article/details/78786646](https://blog.csdn.net/u013064109/article/details/78786646)

### 1.内联扩展函数之let {#2}

let扩展函数的实际上是一个作用域函数，当你需要去定义一个变量在一个特定的作用域范围内，let函数的是一个不错的选择；let函数另一个作用就是可以避免写一些判断null的操作。

```
@kotlin.internal.InlineOnly
public inline fun <T, R> T.let(block: (T) -> R): R = block(this)

let函数适用的场景
场景一: 最常用的场景就是使用let函数处理需要针对一个可null的对象统一做判空处理。
场景二: 然后就是需要去明确一个变量所处特定的作用域范围内可以使用
```

### 2.内联函数之with {#3}

with函数和前面的几个函数使用方式略有不同，因为它不是以扩展的形式存在的。它是将某对象作为函数的参数，在函数块内可以通过 this 指代该对象。返回值为函数块的最后一行或指定return表达式。

```
@kotlin.internal.InlineOnly
public inline fun <T, R> with(receiver: T, block: T.() -> R): R = receiver.block()
```

### 3.内联扩展函数之run {#4}

run函数实际上可以说是let和with两个函数的结合体，run函数只接收一个lambda函数为参数，以闭包形式返回，返回值为最后一行的值或者指定的return的表达式。

```
@kotlin.internal.InlineOnly
public inline fun <T, R> T.run(block: T.() -> R): R = block()

适用于let,with函数任何场景。因为run函数是let,with两个函数结合体，准确来说它弥补了let函数在函数体内必须使用it参数替代对象，
在run函数中可以像with函数一样可以省略，直接访问实例的公有属性和方法，
另一方面它弥补了with函数传入对象判空问题，在run函数中可以像let函数一样做判空处理
```

### 4.内联扩展函数之apply {#5}

从结构上来看apply函数和run函数很像，唯一不同点就是它们各自返回的值不一样，run函数是以闭包形式返回最后一行代码的值，而apply函数的返回的是传入对象的本身。

```
@kotlin.internal.InlineOnly
public inline fun <T> T.apply(block: T.() -> Unit): T { block(); return this }
整体作用功能和run函数很像，唯一不同点就是它返回的值是对象本身，
而run函数是一个闭包形式返回，返回的是最后一行的值。
正是基于这一点差异它的适用场景稍微与run函数有点不一样。
apply一般用于一个对象实例初始化的时候，需要对对象中的属性进行赋值。
或者动态inflate出一个XML的View的时候需要给View绑定数据也会用到，
这种情景非常常见。特别是在我们开发中会有一些数据model向View model转化实例化的过程中需要用到。
```

### 5.内联扩展函数之also {#6}

also函数的结构实际上和let很像唯一的区别就是返回值的不一样，let是以闭包的形式返回，返回函数体内最后一行的值，如果最后一行为空就返回一个Unit类型的默认值。而also函数返回的则是传入对象的本身

```
@SinceKotlin(“1.1”)
public inline fun T.also(block: (T) -> Unit): T { block(this); return this }

适用于let函数的任何场景，also函数和let很像，
只是唯一的不同点就是let函数最后的返回值是最后一行的返回值而also函数的返回值是返回当前的这个对象。
一般可用于多个扩展函数链式调用
```

![](/assets/import.png)



