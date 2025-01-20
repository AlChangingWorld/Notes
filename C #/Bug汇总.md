
## 控制台墙体绘制
Console.WriteLine("■"); 
占x俩个 所以在设置光标位置时 需要空俩格

y = Game.sceneHeight - 1;
在绘制最后一行时 使用WriteLine会导致 自动跳到下一个索引 导致buff区向下移动
改为-2 ,或者使用Write