## 1. ipairs和pairs的区别

ipairs会依据key的数值从1开始加1递增遍历相应的table[i]值。 而pairs则能够遍历表中全部的key，而且除了迭代器本身以及遍历表本身还能够返回nil，可是ipairs则不能返回nil，仅仅能返回数字0,遇到nil则循环退出。
结论：遍历table或array时，如果key是非数字，请使用pairs迭代遍历。

## 2. 函数冒号与点的区别？
冒号定义方法，默认会接受self参数；
而点号定义的时候，默认不会接受self参数

冒号调用方法，会默认地将对象本身(self)传递给方法；而点号调用则不会

## 3. 如何对table新建值时提示错误？
``` lua
function mt:__newindex(key,value) -- 添加__newindex元⽅法 
	mt[key] = nil 
	print("cannot create new property:" .. key..",value="..value) 
end
```

## 4. 深拷贝与浅拷贝
拷贝对象是string、number、bool 那就是互不干涉 深拷贝
拷⻉对象是table表，是浅拷贝 你变我也变

遍历所有的点 进行复制

## 5. 什么是Upvalue？
在lua中，会生成一个全局栈，所有的upvalue都会指向该栈中的值，若对应的参数离开的作用域，栈中的值也会被释放，upvalue的指针会指向自己，等待被gc