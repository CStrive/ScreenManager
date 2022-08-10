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

Once **SimpleTweenScreen** is added, you'll notice few things :
* It added a CanvasGroup element
* It has a lot of strange settings

默认情况下' BaseScreen '类提供了几个重要的设置，这些设置是让屏幕工作得很好的核心

* Generation Settings
 * **Generate Navigation** ( Create explicit navigation so that keyboard/gamepad navigation never leaks to an another screen )
 * **Cancel Selection** ( Button selected or executed when ESC or back button is pressed )
* Cancel Selection
 * **Hide Current** ( Hide previous screen or overlay on top of the previous screen )
 * **Keep on Top when hiding** ( Keep its drawing order on top when hiding )
 * **Layer Priority** ( All screens have layers, imagine that an alert box will block all screen changes that are below it but wouldn't block other alert boxes )
 * **Default Selection** ( Button selected by default when the screen is shown, when left empty : first button found is selected )

You can leave those settings as they are for now, no need for additional configuration.


Once we added **SimpleTweenScreen** to all our screens, we can define our default screen that's going to be open on run.

Go to **ScreenManager** _( Shortcut Ctrl+Alt+T or Window/Select ScreenManager in the menu )_

Select your **SimpleTweenScreen** in the Screens section. 
Once selected you'll see a button named "Set Default" appear. 

Click on it, it will set that screen as the default/main screen.

![ScreenManager](/img/step0.png?raw=true "ScreenManager")

现在已经完成了，我们可以开始设置我们的按钮了。

有两种方法来设置这些按钮 :

![Button](/img/step1.png?raw=true "Button")
![Button](/img/step2.png?raw=true "Button")

你可以通过名称来显示一个屏幕，也可以通过它的GameObject引用来显示。


( Tutorial to be finished )

## 贡献 Contribution
总会有更多的内容需要添加，所以如果你想帮忙，那么请随时投稿 !
