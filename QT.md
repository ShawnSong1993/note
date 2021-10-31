# QT

## 1. 添加资源

1. 单机项目右键，add new
2. 选中Qt-->>Qt resource file
3. 定义file name
4. 将生成的 file name.qrc 添加到 CmakeLists.txt 中， Ctrl + s 保存
5. 右键file name.qrc,选中add in editor
6. add prefix (添加资源标签，方便分类)
7. add file添加图片文件
8. 编译

## 2. 添加自定义窗口

1. 
2. 







```c++
#include "mywidget.h"    //包含应用程序的头文件
#include <QApplication>

//main程序入口  argc命令行的变量数量  argv命令行的变量数组
int main(int argc, char *argv[])
{
    QApplication a(argc, argv);   //应用程序对象，在qt中，应用程序对象有且仅有一个
    myWidget w;   // 窗口对象 
    w.show();    //显示窗口
    return a.exec();   //让应用程序对象进入消息循环 
}
```

```C++
#ifndef MYWIDGET_H
#define MYWIDGET_H

#include <QWidget>

class myWidget : public QWidget
{
    Q_OBJECT     //宏定义，允许使用信号和槽的定义

public:
    myWidget(QWidget *parent = nullptr);    //构造函数
    ~myWidget();    //析构函数
};
#endif // MYWIDGET_H

```

1. 命名规范，

   （1）类的首字母大写，单词的首字母大写

   （2）函数和变量名首字母小写，单词之间的首字母大写

2. 选中某个想要查看的对象，按F1查看帮助文档

## 3. 定时器

1. 定义时间指针     

   ```c++
   QTimer *timer;
   ```

2. 新建指针 

   ```c++
   timer = new QTimer(this);
   ```

3. 连接执行函数 

   ```c++
   connect(timer, SIGNAL(timeout()), this, SLOT(CameraCapture()));
   ```

4. 启动定时器 

   ```
   timer->start(33);
   ```

   

































































