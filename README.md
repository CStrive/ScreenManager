# ScreenManager
灵活的方式来管理你的UI与过渡，层和正确的导航处理Unity

## 简介
* ScreenEditor inspector
* 但整个系统可以通过代码完全使用
* 多层堆栈导航_(alertbox > popup > main)_
  * 可重用屏幕实例
  * 重复屏幕_(弹出，警报)_( popups, alerts )_
* 优化的干净和无臃肿的代码，不需要额外的库
* Button-mashing-proof, screens respect their order and animate in/out properly
* 使用Unity的UI事件进行默认的输入处理_( 包括cancel/back 事件)_
* 用于游戏板和键盘感知导航的始终开启的选定按钮
* **Spread** feature: See all your screens in a grid view for an easier overview and editing
* **Buttons navigation generation**
  * Optional focused default button
  * Cancel/back button which is selected when Cancel key is pressed
  * Isolate navigation to the current screen
* **Extendable generic BaseScreen class**
  * Including pre-made presets: Animate, Tween, AnimationController
  * Easily create your own type of screen using the BaseScreen class
* Mobile tested
* Includes three examples
* Fully documented code

## Gif

![Gif](/img/animated.gif?raw=true "Gif")

_( Note: The inspector window is not forcefully updated, which is why it lags a bit behind )_

## Screenshots

![Screenshot](/img/extension.png?raw=true "Screenshot")
![Screenshot](/img/animatorscreen.png?raw=true "Screenshot")
![Screenshot](/img/screen.png?raw=true "Screenshot")
![Screenshot](/img/spread.png?raw=true "Screenshot")

# Sample code
````
screenmgr.Show("MainMenu");
screenmgr.ShowPopup<Popup>("Alertbox").Message = "Custom Alert Text";
screenmgr.HideAll();
````
## Info


## 如何使用?
只需在任何Canvas元素上创建一个新的ScreenManager
(最好是在主Canvas元素的下方)

暂时不考虑ScreenManager的设置，让我们创建一些屏幕。

首先，我们可以在ScreenManager GameObject下添加SimpleTweenScreen。

对于自定义屏幕。你可以继承`BaseScreen`类或任何其他预制类。_AnimatorScreen，Popup，SimpleTweenScreen，TweenedScreen_。

一旦添加了SimpleTweenScreen，你会注意到几件事:
* 它添加了一个CanvasGroup元素
* 它有很多奇怪的设置

默认情况下' BaseScreen '类提供了几个重要的设置，这些设置是让屏幕工作得很好的核心

* Generation Settings
 * **Generate Navigation** ( 创建明确的导航，使键盘/游戏板导航永远不会泄漏到另一个屏幕上 )
 * **Cancel Selection** ( 当按下ESC或返回按钮时，选择或执行的按钮 )
* Cancel Selection
 * **Hide Current** ( 隐藏前一个屏幕或叠加在前一个屏幕之上 )
 * **Keep on Top when hiding** ( 隐藏时，保持其绘图顺序在顶部 )
 * **Layer Priority** ( 所有的屏幕都有层次，想象一下，一个警报框会阻止所有在它下面的屏幕变化，但不会阻止其他警报框。 )
 * **Default Selection** ( 当屏幕显示时默认选择的按钮，当留空时：找到的第一个按钮被选中。 )

你可以暂时保留这些设置，不需要进行额外的配置。


一旦我们把**SimpleTweenScreen**添加到我们所有的屏幕上，我们就可以定义我们的默认屏幕，它将在运行时被打开。

进入**ScreenManager** _( 快捷键Ctrl+Alt+T或Window/Select ScreenManager in menu )_。

在Screens部分选择你的**SimpleTweenScreen**
一旦选定，你会看到一个名为 "Set Default "的按钮出现。

点击它，它将设置该屏幕为defaul/main screen。

![ScreenManager](/img/step0.png?raw=true "ScreenManager")

现在已经完成了，我们可以开始设置我们的按钮了。

有两种方法来设置这些按钮 :

![Button](/img/step1.png?raw=true "Button")
![Button](/img/step2.png?raw=true "Button")

你可以通过名称来显示一个屏幕，也可以通过它的GameObject引用来显示。


( Tutorial to be finished )

## 贡献 Contribution
总会有更多的内容需要添加，所以如果你想帮忙，那么请随时投稿 !
