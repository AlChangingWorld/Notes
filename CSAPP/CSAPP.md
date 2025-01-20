# Computer System: A programmer's Perspective (Third Edition)

## 主要内容

本书是以程序员视角来看待计算机系统，即从代码到底层实现直接所涉及的计算机系统软件与硬件系统知识. 是对计算机系统的整体进行梳理，一本入门书籍.

 B站视频[链接](https://www.bilibili.com/video/BV1iW411d7hd/?spm_id_from=333.1007.top_right_bar_window_default_collection.content.click&vd_source=0c4d3757f8e8cc383a6cf67d0c38419d).

## 一、Int and float

Example:

40000 \* 40000 = 1600000000;

50000 \* 50000 = -1794967296; -------???

(1e20 +-1e20) + 3.14 = 3.14

1e20 + (-1e20 + 3.14) = 0 -----???

## 二、Assemly 汇编语言

## 三、Memory matter 内存问题

```c++
class struct_t
{
    public:
        int a[2];
        double d;
};
double fun(int i)
{
    struct_t s;
    s.d = 3.14;
    s.a[i] = 1073741824;
    return s.d;
}

int main()
{
    cout <<"0    " << fun(0) << endl;
    cout <<"1    " << fun(1) << endl;
    cout <<"2    " << fun(2) << endl;
    cout <<"3    " << fun(3) << endl;
    //cout <<"4    " << fun(4) << endl;
    //cout <<"5    " << fun(5) << endl;
    //cout <<"6    " << fun(6) << endl;
}

fun(0)---->3.14
fun(1)---->3.14
fun(2)---->3.14 -------???
fun(3)---->2    -------???
```
## 四、Optimize performance
``` c++

void copyij(int src[2048][2048], int dst[2048][2048])
{
    int i, j;
    for ( i = 0; i < 2048; i++)
    {
        for ( j = 0; j < 2048; j++)
        {
            src[i][j] = dst[i][j];
        }
    }
}

void copyji(int src[2048][2048], int dst[2048][2048])
{
    int i, j;
    for (j = 0; j < 2048; j++)
    {
        for (i = 0; i < 2048; i++)
        {
            src[i][j] = dst[i][j];
        }
    }
}
俩个函数功能相同但所需时间不同.
```





