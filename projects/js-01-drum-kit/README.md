## 📚 学习来源与致谢
本项目是跟随 [JavaScript 30](https://javascript30.com/) 课程的 **“JavaScript Drum Kit”** 练习所完成。
- **教程作者**：Wes Bos
- **代码实现**：在理解课程核心思路后独立编写完成。
- **音频资源**：使用了课程提供的原始鼓点音效文件。
#JS-01-drum-kit（鼓点模拟器）
##这是JavaScript30天挑战的第一个项目。
##实现功能
- **键盘演奏**：按压 `A` `S` `D` `F` `G` `H` `J` `K` 键触发不同鼓点音效。
- **视觉反馈**：按键时对应键位有缩放与边框高亮动画。
- **响应式界面**：适配不同屏幕尺寸
##技术栈与核心知识点
- **HTML**:
<div class=“keys”>：
这里的class=“keys”是一个CSS类名，用于格式化，是JavaScript中选择整个键盘区域的“钩子”。
<div data-key=“65” class=“key”>：
①这个标签是连接键盘、屏幕和声音的“数据锚点”，运用的是data-*自定义数据属性的技术。
②首先，在HTML中，我们为视觉按钮和音频文件都加上了此键码，此时<div>和<audio>中会有一一对应的data-key，建立了字母和音频文件的一对一关系；
③然后，事件触发，当我按下键盘上的“A”这个按键，浏览器就会随即产生一个keydown事件，并且自动生成一个事件对象e，这个e就像一个大箱子，它里面装了很多信息，其中就包含：e.keyCode 等于 65；
④最后，JavaScript函数，整个浏览器窗口被挂上了监听器（window.addEventListener('keydown', playSound)），意思是只要有人按下键盘上的任意键（keydown事件），就立刻去调用 playSound 这个函数，于是，playSound(e) 函数被自动调用执行，参数 e 里就装着 keyCode: 65，函数开始运行，找到对应的标签（<div>,<audio>）,然后播放声音添加动画。
- **CSS3**: 
①.playing {}->动画触发器
主要是设计缩放动态效果
②.keys {}->弹性盒子布局
align-items: center; justify-content: center;：Flex布局的经典居中组合。前者垂直居中，后者水平居中。
- **JavaScript**: 
①removeTransition(e){}->当按键的缩放动画完全结束后，自动移除高亮样式，让按钮恢复原状。
②playSound(e) {}->根据用户按下的键（e.keyCode），精准定位到对应的 <audio> 标签来播放声音，并定位到对应的 <div> 标签来触发视觉动画。
③window.addEventListener(‘keydown’, playSound)->监听全局键盘按下事件。
##学习收获与难点：
- html是骨架，CSS是装饰，Javascript是神经。我深刻理解了“数据驱动”的现代前端思想，理解了它们如何通过 data-key 这个自定义属性（数据桥梁）联动。
- 弄懂了 addEventListener 如何作为总开关，将用户操作（键盘按下）转化为函数调用。理解了从 keydown 事件发生，到 playSound 函数被触发，再到内部查询执行的完整事件流。
- 感受到贯穿整个前端开发的“状态驱动视图”的思想。
- 完整地完成了一个小型开发项目，迈出了第一步！
   