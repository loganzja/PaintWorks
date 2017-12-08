# PaintWorks

## 已实现的功能

* 直线绘制
* 圆的绘制+填充
* 椭圆绘制
* 多边形绘制+填充
* 已实现基础的UI交互，切换图形绘制模式
* 已实现markDraw，为各Figure提供被选中的虚线矩形框显示
* 已实现**图形编辑**
* 已实现**图形变换**
  - 平移：已实现各图形的平移（通过点的平移实现）
  - 旋转：已实现各图形的旋转（其中圆的旋转保持不变，椭圆旋转只能转90度）
  - 缩放：已实现各图形的缩放（直线以中点为准，圆和椭圆以中心为准，多边形以绘制的第一个点为准）

## 下一步工作

* **图形裁剪**
* **存储图形数据**
* **3D多面体显示**
* **曲线绘制&编辑**


## 目前进展

* 解决了MainWindow直接控制当前GLWidget的问题

  使用`dynamic_cast<GLWidget*>()`即可，可以不必再使用GLWidget的数组canvases(已去掉)

* 实现了直线裁剪

  裁剪时对所有直线均进行裁剪

* 添加了UI

  * 放大缩小

    对所有图形同时放大缩小，缩放基准点为各图形自己的基准点，而非鼠标

  * 填充

  * 裁剪

  * 平移

    * 直线拖动中点平移
    * 圆拖动圆心平移
    * 椭圆拖动中心平移



## 可以改进的地方

* 缩放的基准点改为鼠标
* 交互界面新增按钮
  * 平移：拖动矩形中心点
  * 旋转：拖动延伸出来的点

## bug

* ~~标签页关闭之后切换图形绘制模式会导致程序崩溃~~ 已使用dynamic_cast解决

  应该让QMdiSubWindow在关闭时delete掉GLWidget，可能需要重写QMdiSubWindow的` virtual void	closeEvent(QCloseEvent * closeEvent)` 函数，最好是将相关信号关联到Mainwindow的一个槽函数，省得再写QMdiSubWindow了。