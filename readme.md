## whichDisneyAreYou

很多朋友前阵子可能在各大平台上看到过一款滤镜『你是迪斯尼的哪个角色 whichDisneyAreYou』，其实这是 Instagram 平台的一款滤镜，但并非官方推出，而是用户自己制作，那么如何制作自己的 Instagram 滤镜呢？今天就来全方位教你！

先来看看最终效果，我做的『你是哪个神奇宝贝 whichPokemonAreYou』滤镜（网站展示的 GIF 效果不是很好）。

![img](https://cdn.sspai.com/2020/03/27/01f5337c9fa448040468bd9493c0aba4.gif)which Pokemon are you？

## 前期准备

1. 首先需要一个 Instagram 账号，或者 Facebook 账号，在这两个平台都可发布自己的滤镜。
2. 下载 Facebook 官方推出的制作滤镜的工具 [Spark AR Studio](https://sparkar.facebook.com/ar-studio/)。

![img](https://cdn.sspai.com/2020/03/26/214ec5e6371395f250f1a4e2152d8fad.png)Spark AR Studio

 

## 制作滤镜包括哪几方面？

首先来大致列一下制作滤镜需要考虑哪些方面的内容：

1. 素材：主要包括你要用在滤镜中的图片素材，比如 Pokemon 滤镜中的『问题页』图片，和各个神奇宝贝的图片；
2. 场景：要将这些素材内容放在什么位置，比如在头部上方；
3. 逻辑：使用什么逻辑来控制滤镜，例如如何触发各种特效。

然后来了解一个这款滤镜编辑器的主要功能区。

左上角是场景区域，左下角是素材区，中间上方用来预览你的滤镜效果（默认就是一个黑人小哥一直摇头晃脑展示你的滤镜），中间下方是滤镜的所有逻辑（如果没有这个区域，可以在菜单栏 View 中打开），右方是属性区。

![img](https://cdn.sspai.com/2020/03/26/33daf69f332c4870c402aad2be08a7fd.png)编辑器主界面

## 开始制作滤镜

下面我就以这个 Pokemon 滤镜为例，展示一下如何从头开始制作一款滤镜。由于这款滤镜逻辑之复杂，相信你做过这款滤镜后再无惧任何滤镜的制作哈哈。

首先我们来设想一下这款滤镜的最基础功能：

1. 在头部上方出现 which Pokemon are you 的图片；
2. 等待一小段时间；
3. 开始出现各个神奇宝贝的图片，并快速切换；
4. 等待一小段时间；
5. 图片停在某一个神奇宝贝。

等一下，你是否曾有一瞬间认为这种滤镜的匹配并非随机，而是各种人脸识别深度学习？但显然没有这么高级，之所以有时候给人好像最终选择的图片和人有相似之处的错觉，可能是人们会主动去寻找相似之处。~~咦，这不是星座学吗？？~~

按照我们之前提到的三部分，来一步步进行滤镜的制作：

### 添加素材：

1. 放入问题页的素材：点击菜单栏 Add -> Material 来添加素材，命名为『question』，点击 Texture -> Choose File 选择提前准备好的『问题页』图片，你会看到左下角出现一个 Textures 里包含了你选择的图片。
2. 放入神奇宝贝序列的素材：再次点击菜单栏 Add -> Material 来添加素材，命名为『answer』，点击 Texture 中**左边的箭头**，选择 New Animation Sequence 建立一个动画序列，在这个动画序列里点击 Texture -> Choose File，**同时选择**你要循环播放的**所有图片**，这些图片就会自动形成一个动画序列。

![img](https://cdn.sspai.com/2020/03/26/359f48e1ac9eb4b962a91397116125d7.png)完成素材添加

## 添加场景：

1. 建立场景：因为我们希望将图片固定在头部上方的位置，随着人头移动，因此点击 Add -> Scene Understanding -> Face Tracker 添加一个脸部跟踪器。
2. 因为我们的图片效果是平面，右键 Face Tracker 点击 Add -> Plane，点击 Plane，在其属性栏的 Material 中 + 添加前面定义的 question。在中间上方的区域，可以移动、旋转或缩放该图片，也可以直接在属性栏定义，我们将图片上移到黑人的额头。
3. 继续添加定义好的动画序列，一样的步骤：右键 Face Tracker 点击 Add -> Plane，点击 Plane，在其属性栏的 Material 中 + 添加前面定义的 answer。将它调整到和 question 一样大小和位置，可以直接复制 question 的九个参数。

![img](https://cdn.sspai.com/2020/03/26/eeaed57e01cfb31274195dff94c137b0.png)完成场景添加

### 添加逻辑：

终于到了最复杂的地方了... 此时不妨再回顾一下这款滤镜的功能逻辑。

1. 首先是滤镜的开始条件，也就是用户开始录像：右键左上角 Scene 中的 Camera，点击 Create Patch，可以看到逻辑区出现了紫色的 Camera 模块，右侧四个箭头表示 Camera 的四个触发条件，最下面一个是我们需要的开始录像。
2. 添加一个计时器，控制时间触发条件：右键逻辑区的空白处，搜索 Runtime 添加，按住右侧箭头拖到空白处松开，在弹出框搜索 Offset，用来记录时间，再按住 Offset 右侧箭头拉出，添加 Less Than，将它的时间设置为 1.5 秒。
3. 小于 1.5 秒时出现问题页，大于 1.5 秒时出现答案页，因此先添加控制出现与否的模块。选择左上角 Scene 中的 plane0，也就是问题页，在属性栏中的 Visible 点击左侧箭头，逻辑区出现黄色模块，对 plane1 也就是答案页进行一样的操作。
4. 将 Less Than 的右侧连接到 question 的左侧，再拉出 Less Than 的右侧，选择 Not 函数，将 Not 连接到答案页。点击编辑器最左侧边栏的刷新按钮，可以看到黑人头上已经实现了根据时间切换问题与答案的效果。

![img](https://cdn.sspai.com/2020/03/26/5839a0c95d552c5967a81e5038db1801.png)实现根据时间切换问题与答案

1. 要将动画在某个时间点停下来，从 Offset 再拉出一个 Less Than，设置为 4 秒，拉出一个 Loop Animation，这是用来循环的，将循环时间改短一点，比如 0.001，再用下方箭头 looped 拉出一个 Random，这是用来随机数字的，将 End Value 设置为答案页图片的数量，这边做的就是不断随机出数字，然后在时间到 4 秒时的那个数字赋给动画序列，决定最终选择的是序列的第几帧。
2. 点击素材区的 answerSequence，点击属性区的 CurrentFrame 左侧箭头，将上一步的 Random 接到 CurrentFrame。此时再刷新一次，可以看到实现了四秒时停在某一帧的效果。离胜利越来越近了！

![img](https://cdn.sspai.com/2020/03/26/393866f69f273690ee22f98fa0c64399.png)完成动画停在随机一帧

最开始的 Camera 模块还没用到，将最下面的箭头连到 Offset 下面的 Reset 箭头，表示开始录像的时候重置计时器。

至此，我们基本上完成了这个滤镜的功能啦！

### 最后完善

如果你只是想简单了解做滤镜的过程，那么到这边就可以啦！但如果想把这款滤镜做好，还需要一些完善。

本来看上去已经很美好了，但是实际用了之后，就会发现还有一点体验上的小问题，主要是：

1. 用户选择这个滤镜后，如果不开始录影，计时器依旧自动运行，导致整个逻辑直接跑完了。用户还没玩就知道会发生什么，这显然不太好。
2. 用户录屏结束后，想重新玩，但此时没有自动回到问题页，因为只有开始录屏才会重置计时器，结束录屏并不会重置。

分析这两个原因，要加的逻辑主要以下两点：

1. 出现答案页的条件不仅是大于 1.5 秒，还需要已经开始录屏，因此添加一个 And 函数，从 Camera 的 Pulse 拉出 Switch 函数，删除连到 Flip 的线，将 On 和 Off 对应连接上，从 Less Than（1.5）拉出 Switch 函数，将 On 和 Off 反着连接（为啥？），将两个 Switch 的输出分别连到 And 函数的输入。
2. 将之前 answer 前面的 Not 函数换到 questio(plane0) 的前面（又为啥？？），将 And 和 Not 连接，And 和 answer(plane1) 连接，最终结果见下图。

![img](https://cdn.sspai.com/2020/03/26/54240752f5f675ea5ad71811a1407fda.png)伟大工程终于完成

一个完美主义者的滤镜终于完成了！

### 测试和上传滤镜：

在最左侧边栏的下方，有测试和上传滤镜的按钮，测试可以绑定账号，发送到 App 进行测试，也可以直接连接设备进行测试。测试完成后，可以提交滤镜，注意滤镜具体大小的限制（Instagram 平台 4M，Facebook 平台 10M），所以你的图片素材不要太大。

完成后，去网站中将滤镜的各种信息填写完整，就可以提交审核啦！

# whichPokemonAreYou

在网站中可以看到自己的滤镜被多少人观看、拍摄和分享。这是我的滤镜现在的数据，虽然称不上“爆款”，但你做的滤镜一定可以成为爆款！

![img](https://cdn.sspai.com/2020/03/26/ecc477d759830d3d0e2b369322016963.png)我的滤镜数据

这个编辑器里还有许多功能可以探索，尽情发挥你的想象力！



同时，抖音也有自己的滤镜编辑器，但功能没有这个强大，有兴趣的同学也可以玩一玩，基本功能是类似的。（抖音的用户自制滤镜排行榜常年被土味滤镜霸占）