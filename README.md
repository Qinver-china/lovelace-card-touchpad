# lovelace-card-touchpad for homeassistant lovelace UI
### 用于homeassistant的lovelace的一个触摸板卡片

去年我发布过一个[more-info-qinver-tv](https://github.com/Qinver-china/homeassistant-Custom_UI_more-info-qinver-tv)的自定义详情页，初衷就是为了解决homeassistant不方便触摸操作的问题，因为像很多类似于电视遥控器的控制，如果只能点击按钮，那么在移动设备上的体验是很糟糕的！

现在过去一年多了，几乎我也有一年多没有玩homeassistant了，最近无聊升级了最新的0.99，显而易见，之前的more-info-qinver-tv自定义详情页不能再使用了。

现在homeassistant的前端基本都使用了[lovelace UI](https://www.home-assistant.io/lovelace/)，确实很方便，自定义空间更大了

这一次，我重新设计了这样的一个功能，整体想法是制作一个触摸面板，在这个面板上，你可以点击、双击，滑动以控制HA的各种设备，用来当作遥控器最合适不过了，当然也不仅仅是遥控器了，或许你能有更好的用处！

## 目录
* [更新记录](#更新记录)  
* [功能介绍](#功能介绍和截图)  
* [开始使用](#安装以开始使用)  
* [与我联系](#与我联系和反馈) 
## 更新记录 
2019年10月7日
首次发布

## 功能介绍和截图
```  
正如下面截图一样，就是一个面板，你可以在这个面板上面点击、滑动来控制HA的设备，大致的功能和特色如下： 
1. 支持的操作：单击、双击、上下左右滑动和上下左右长滑动
2. 每一个操作动作均有动画反馈
3. 触摸板的上方和下方均可以增加额外的按钮
4. 触摸面板可选择是否折叠
5. 配置文件十分简单，几乎所有的配置代码都可以选择性删除
```

![效果图](https://raw.githubusercontent.com/Qinver-china/lovelace-card-touchpad/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE/%E8%A7%A6%E6%91%B8%E6%9D%BF.jpg)    

## 安装以开始使用：
1. 下载本仓库的`www/lovelace-card-touchpad.html`文件放入到你homeassistant配置文件目录的`~~/www`文件夹下  
如图所示：  
![](https://raw.githubusercontent.com/Qinver-china/lovelace-card-touchpad/master/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE/%E6%88%AA%E5%9B%BE1.jpg)  
2. 在homeassistant配置文件`ui-lovelace.yaml`中的对应位置加入以下代码，以加载lovelace-card-touchpad
```yaml
resources:
  - url: /local/lovelace-card-touchpad.html
    type: html
```  
3. 在`ui-lovelace.yaml`加入对应的以下配置文件代码即可。
完整的配置文件示例代码如下，你需要把相应的ID换成你的就可以了
```yaml
    cards:
      - type: custom:lovelace-card-touchpad   #必须
        ####  以下内容均为可选，不需要的删了那一行就行
        name: 客厅电视遥控器
        icon: mdi:television
        fold: true    #折叠触摸板
        debug: true   #显示调试信息
        touchpad:               #以下是触摸板功能的ID
          tap: script.tap               #单击
          up: script.up                 #上滑
          down: script.down             #下滑
          left: script.left             #左滑
          right: script.right           #右滑
          double_tap: script.double_tap       #双击
          Long_up: script.Long_up             #长上滑
          Long_down: script.Long_down          #长下滑
          Long_left: script.Long_left          #长左滑
          Long_right: script.Long_right        #长右滑
        top_buttons:    ##触摸板 上面的 按钮
          - switch.xxxxxx_1
          - switch.xxxxxx_2
          - switch.xxxxxx_3
        bottom_buttons:    ##触摸板 下面的 按钮
          - switch.xxxxxx_4
          - switch.xxxxxx_5
          - switch.xxxxxx_6
```
配置文件注意事项：
1. 你可能觉得以上配置文件有点复杂，其实并不是，上面的配置文件的每一行都是可以删除的，比如说你只需要一个触摸板，不需要额外的按钮，那就把按钮部分的代码删了就是了，甚至什么名称、图标的什么的都可以删除，包括触摸板功能，也可以删除的！
2. 配置文件touchpad的触摸功能建议使用`script`的服务的ID，因为这种不需要状态反馈。`top_buttons`和`bottom_buttons`可以随意，但不支持传感器

## 与我联系和反馈
欢迎浏览我的个人博客[倾微博客](http://blog.qiwe.ink)   
欢迎加入[『瀚思彼岸』](https://bbs.hassbian.com)论坛   
如果遇到问题请在[这个帖子](https://bbs.hassbian.com/thread-4024-1-1.html)中提交回复   



