
## 1. 奥德赛项目移动问题 3个小时

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
//这个方法的作用是处理输入的“死区”。
//死区是指当输入值非常小（比如摇杆的中心点）时，不考虑其影响，避免微小的噪声值引起不必要的移动
public virtual Vector3 GetAxisWithCrossDeadZone(Vector2 axis)
{
    // 获取死区值
    var deadzone = InputSystem.settings.defaultDeadzoneMin;

    // 处理水平轴（x） 大于死区进行下一步
    axis.x = Mathf.Abs(axis.x) > deadzone ? RemapToDeadzone(axis.x, deadzone) : 0;
    // 处理垂直轴（y） **这一步复制的上面代码 axis.x **
    axis.y = Mathf.Abs(axis.y) > deadzone ? RemapToDeadzone(axis.y, deadzone) : 0;

    // 将处理后的 x 和 y 转换为一个 Vector3，其中 y 变成了 z 分量
    // 因为你键盘的输入是2D的 不参与y轴 所以 2D要转成3D
    return new Vector3(axis.x, 0, axis.y); 
}
```