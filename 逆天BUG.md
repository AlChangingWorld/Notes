## 1. 控制台墙体绘制
Console.WriteLine("■"); 
占x俩个 所以在设置光标位置时 需要空俩格

y = Game.sceneHeight - 1;
在绘制最后一行时 使用WriteLine会导致 自动跳到下一个索引 导致buff区向下移动
改为-2 ,或者使用Write

## 2. 奥德赛项目移动问题 3个小时

**出BUG原因**
发现w和s输出不能接收到 所以不能在ws方向上移动 
原来是复制的时候 没改 粗心大意

**收获**
如何使用Unity和VS来不断的调试检查错误 
需要先将VS代码运行 然后运行Unity项目
F5跳过 F10下一步 不进入 F11进入内部 可以拖动来回到之前步骤 
在找不到下层的代码时 可以利用F10来跳
可以看堆栈中的调用顺序

**感想**
检查过的地方不用看 一次次的缩小范围 锁定出错的地方
重点是在于别放弃哟！

``` c#
axis.x = Mathf.Abs(axis.x) > deadzone ? RemapToDeadzone(axis.x, deadzone) : 0;
// 处理垂直轴（y） **这一步复制的上面代码 axis.x **
axis.y = Mathf.Abs(axis.y) > deadzone ? RemapToDeadzone(axis.y, deadzone) : 0;
```

## 3. 奥德赛项目向后转会飞起来 1个小时
在Brake到Backflip时 会给竖直方向一个速度 不知道为什么 
原来是后空翻 跳一下来转到后面 不然不顺畅
调试还是能发现问题