# Kotlin JVM常用注解参数解析

官方注解地址：[https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.jvm/index.html](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.jvm/index.html)

参考文档：[https://www.jianshu.com/p/2ca358b6db3d](https://www.jianshu.com/p/2ca358b6db3d)

今天我们来学习和理解这些常用的注解：

`JvmDefault JDk1.8+`interface 里的default声明

`JvmField 使Kotlin编译器不再对该字段生成getter/setter并将其作为公开字段（public）`

`JvmMultifileClass 这个注解让Kotlin编译器生成一个多文件类，该文件具有在此文件中声明的顶级函数和属性作为其中的一部分，JvmName注解提供了相应的多文件的名称.`

`JvmName 这个注解的主要用途就是告诉编译器生成的Java类或者方法的名称`

`JvmOverloads 告诉Kotlin编译器为此函数生成替换默认参数值的重载 ，只有有默认值的参数会参与重载.`

`JvmStatic 此注解只能在companion object中使用，消除Java调用Kotlin的companion object对象时不能直接调用其静态方法和属性的问题.`

`Strictfp 将从注释函数生成的JVM方法标记为strictfp，意味着需要限制在方法内执行的浮点运算的精度，以实现更好的可移植性。`

`Synchronized`

`Volatile`

`Transient`



