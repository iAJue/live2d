# Live2d 看板娘
前段时间，在不少人博客看到这个 Live2D 看板娘，颇感兴趣！就查阅了点相关教程为自个博客也添加上了
前言
live2d并不是一种先进的技术，它产生的效果，都是用基本的平移、旋转、透明、曲面变形等操作实现的。最终的效果与贴图关系很大，而每一个动作，都需要制作师的精细调整。这是一个需要消耗大量时间精力的过程，因此质量好的模型并不多，质量好的也一般是在游戏中，版权受到保护，不能随意使用。
本文章中所用模型解包自药水制作师手机游戏，版权归该官方所有。(没错，我也是来安利这款游戏的)
准备工作

俗话虽说：“授人以鱼不如授人以渔”，但是由于这鱼比较难钓，我们还是乖乖搬个小板凳坐吃鱼群众吧！
以下代码是我光明正大从后宫学长那偷过来的鱼加以烹饪而成。

先到我的 Github 去下载我再次整理过后的live 2D的代码(包含两人的动作和初始的三套贴图)，毕竟还是煮熟的好吃点~
下载后解压代码到你的博客网站根目录去。（目录位置可以自定义）
然后把解压出来的文件夹改名为：live2d 。（叫啥无所谓，好看最重要）
(少女盲目分析中)

食用方法

然后就教大家怎么吃吧，呸，还真吃起来了
在你博客程序头部文件（header.php）引入界面样式，在 head 标签内插入如下代码：
 <link rel="stylesheet" href="/live2d/css/live2d.css" />

在你博客程序页脚文件（footer.php）引入脚本，在 body 标签结束前插入如下代码：
<script type="text/javascript">
    var message_Path = '/live2d/'
    var home_Path = 'https://www.52ecy.cn/'  
</script>
<script type="text/javascript" src="/live2d/js/live2d.js"></script>
<script type="text/javascript" src="/live2d/js/message.js"></script>
<script type="text/javascript">
    loadlive2d("live2d", "/live2d/model/tia/model.json");
</script>
以上代码在使用绝对路径时要注意一个问题：
像我博客 www.52ecy.cn 和 52ecy.cn 都可以进行访问，但是如果在引用的时候使用了www，访问www.52ecy.cn的时候是没有问题，但在直接访问52ecy.cn的时候，会因为跨域问题(子域名不同也属于跨域)，导致json无法加载，然后你的看板娘就出不来了。
可以改为以下代码(人物的切换也只需改为相应的文件夹名字即可)
<script type="text/javascript">
    loadlive2d("live2d", "<?php echo 'http://'.$_SERVER['HTTP_HOST'].'/'; ?>live2d/model/Pio/model.json");
</script>

在合适的页面位置插入 Live2D 看板娘的元素，可以放在底部：
但不建议直接使用，可能会和模板样式冲突，按自己的情况做适当修改
<div id="landlord">
    <div class="message" style="opacity:0"></div>
    <canvas id="live2d" width="280" height="250" class="live2d"></canvas>
</div>

鼠标放在页面某个元素上时，需要 Live2D 看板娘提示的请修改 message.json 文件。
{
    "mouseover": [
        {
            "selector": ".container a[href^='http']",  //此处修改为你页面元素的标签名
            "text": ["要看看 {text} 么？"]  //此处修改为你需要提示的文字
        },
        {
            "selector": ".navto-search",
            "text": ["在找什么东西呢，需要帮忙吗？"]
        }
    ],
    "click": [  //此处是 Live2D 看板娘的触摸事件提示
        {
            "selector": "#landlord #live2d",
            "text": ["不要动手动脚的！快把手拿开~~", "真…真的是不知羞耻！", "再摸的话我可要报警了！⌇●﹏●⌇", "110吗，这里有个变态一直在摸我(ó﹏ò｡)"]
        }
    ]
}

然后，刷新你的博客页面，看看效果吧！

注意路径别弄错了噢 ~
使用主题函数获取路径其实是很好的。
建议都使用绝对路径进行引用，而不是像列子中的相对路径
成品效果欣赏

Pio

Tia

喵的，万恶的水印你走开！
具体效果你可以调戏一下本博客左下角的Pio(没错，我觉得她更可爱)
结语

关于如何进行换装play 请参考原作者(猫和向日葵)的这篇文章 给博客添加能动的看板娘(Live2D)-关于模型的二三事
请注意本文中出现的“药水制作师”、“Potion Maker”字样及应用内包含的文本、模型、图片、动作数据等所有权均属于“药水制作师”作者Sinsiroad，仅供研究学习，不得用于商业用途
