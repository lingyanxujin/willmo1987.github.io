---
layout: post
title: LinearLayout和RelativeLayout
categories: Android
tags: layout UI
---

###缘由

&emsp;&emsp;上周末在家上网看技术文档，无意中发现一哥们儿的[Blog](http://stormzhang.github.io/)，界面干净整洁，结构清晰，颜色搭配也很舒服，于是非常有阅读的欲望。这里解释一下，我这人有点洁癖的，这不光体现在生活中，写代码或文档也是。以往查资料的时候，也看过非常多的Blog，转载的，或转载不注明出处的就不提了，有些原创的Blog实在是没法看，排版乱七八糟，要不是为了解决问题，实在是一眼都不想看。所以像这类排版整齐界面干净的Blog还是比较吸引我眼球的，顿时就有了非常想阅读的欲望。于是我就挑了一些自己比较感兴趣的几篇看起来了，其中有一篇讲到[Android的布局优化](http://stormzhang.github.io/android/2014/04/10/android-optimize-layout/)，文章从Layout的选用、include标签、merge标签和ViewStub标签四个方面介绍了怎样优化Android的布局，其中大部分的内容我还是比较赞同的，唯独LinearLayout相对RelativeLayout的性能更好一点我不是很同意，所以今天有这个冲动想发表一下我的看法。

###我眼中的LinearLayout和RelativeLayout

&emsp;&emsp;LinearLayout和RelativeLayout都是Android的基本控件，特点如下：

1. LinearLayout：线性布局，用法简单，只要设置orientation为vertical或horizontal就可以控制其内部子View的排列是纵向还是横向
2. RelativeLayout：相对布局，配置比较繁多，诸如align系列和alignParent系列等等，但是灵活性强，对于较复杂的布局可以减少Layout的层数

&emsp;&emsp;上面提到的Blog中推荐使用LinearLayout，因为性能比RelativeLayout稍高，我认为不是，这两种Layout都是最基本的Layout控件，都是Google优化过的产物，各有各的作为，如果硬要拉在一起比较的话，性能上的差距微乎其微，甚至我认为RelativeLayout的性能要略优于LinearLayout，不知道大家有没有注意过，每次新建工程的时候，默认MainActivity的layout文件都是RelativeLayout。抛开上面的比较，这并不是我今天想表达的东西，上面我也说了，LinearLayout和RelativeLayout在性能上的差距是微乎其微的，完全可以忽略，我们完全没有必要在比较RelativeLayout和LinearLayout上费劲力气。

&emsp;&emsp;一个好的布局或者说一个最优的布局设计，他的Layout层数一定是最精简最少的，单纯的RelativeLayout或者单纯的LinearLayout可能达不到这样的效果，这时我们就需要搭配着来使用。发挥他们各自的长处达到我们需要的最好的效果，这才是我想表达的想法。对于布局的搭建或者说Layout的使用，可以总结为下面几点：

1. 尽量减少Layout的层数，有时候需要merge标签的帮忙
2. 看情况搭配使用RelativeLayout和LinearLayout
3. 不要滥用LinearLayout，尤其是layout_weight属性，这是一个比较耗性能的属性，慎用！

###总结

&emsp;&emsp;比较RelativeLayout和LinearLayout的目的就是为了搭建一个性能较好的布局，但是这两个最基本的Layout控件都是Google精心设计优化过的，性能上的差距可以忽略，比较也没有意义，只要记住我一上总结的三点，做出来的就是一个性能最优的布局。
    另外再附上一篇[Android官方的开发者博客](http://android-developers.blogspot.com/2009/02/android-layout-tricks-1.html)，里面介绍了一个使用RelativeLayout的小技巧—android:layout_alignWithParentIfMissing属性的使用，我也是头一回见，涨姿势啊！

####注：关于layout_weight的配置和计算方法我计划在下一篇博客中详细解释，为什么要设置宽度为0dp，好像match_parent也没问题？