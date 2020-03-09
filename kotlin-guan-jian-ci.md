```
internal
```

```
infix  修饰符代表该函数支持中缀调用
例如：infix fun Any.to(that:Any) = Pair(this,that)
然后为任意对象提供扩展函数 to，接受任意对象作为参数，最终返回键值对。
```

```
inline
把这个函数的函数体复制到所有调用到它的地方.形参也会被复制到这个方法内使用到的地方.
```

```
oninline
inline中默认都是都是inline的，如果函数传递函数就容易出问题，需要用oninline
```



