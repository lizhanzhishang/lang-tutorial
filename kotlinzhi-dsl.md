[Anko Layouts](https://link.jianshu.com/?t=%28https%3A%2F%2Fgithub.com%2FKotlin%2Fanko%29) 是经典的DSL。

关键点是：扩展函数、lambda、中缀调用和 invoke 约定。

1.对于同样作为静态语言的 Kotlin 来说，扩展函数（扩展属性）是让他拥有类似于动态语言能力的法宝，即我们可以为任意对象动态的增加函数或属性。

```
为 String 扩展一个函数： lastChar():

fun String.lastChar(): Char = this.get(this.length - 1)
```

### ![](/assets/importx.png)![](/assets/impxort.png)

### Kotlin 的 lambda 有个规约：如果 lambda 表达式是函数的最后一个实参，则可以放在括号外面，并且可以省略括号，如：

```
person.maxBy({ p:Person -> p.age })

// 可以写成
person.maxBy(){
    p:Person -> p.age
}

// 更简洁的风格：
person.maxBy{
    p:Person -> p.age
}
```

![](/assets/2132、.png)

![](/assets/impodsadasrt.png)

![](/assets/idasdsamport.png)

![](/assets/imdsadport.png)

## 中缀调用

![](/assets/imzgonduiport.png)

![](/assets/impdsadasort.png)

## invoke 约定

Kotlin 提供了 invoke 约定，可以让对象向函数一样直接调用，比如：

