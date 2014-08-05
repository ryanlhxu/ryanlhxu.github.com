---
layout: post
title: 媒体与政治
description: "基于博弈的框架"
category: Economics
tags: [Policy,Economics, Media, Game Theory]
comments: true
---
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

### 回顾

之前已经有实证的证据表明，美国政治在1879年到1935年政治的极化程度下降，1935到1970年基本保持不变，但在1970年以后极化程度上升。总的看来，大体上是随时间U型变化的趋势。本文提供了一个假说，认为这与媒体的集中度有关。高的媒体集中度（垄断）会减少政治的极化；而低的媒体集中度（竞争）增加政治的极化。

<br/>

在本文的模型中，以美国政治为例，有两个政党，一个是民主党，一个是共和党。两党可以制定自己的执政政策，党派的效用只与最终被执行的政策有关。想象有一条以原点为中位的坐标轴，民主党位于负端，而共和党位于正端。党派可以在$$[-\frac{1}{2},\frac{1}{2}]$$上选择自己的政策。对于民主党来说，最合意的政策执行点是$$-\frac{1}{2}$$；而对于共和党来说，最合意的政策实施点为$$\frac{1}{2}$$。在均衡中，民主党制定的政策$$p_{-1}$$位于负轴上，而共和党制定的政策$$p_{1}$$位于正轴上。简单起见，由于对称性，在均衡中有$$p_{-1} \leq p_{1}=p_{-1}$$。

<br/>

最终的政策由执政党执行，执政党由选民选举产生，选举采取多数战胜少数原则。所以，获得更高票数的政党获得执政权，执行自己的政策，并且他们不能改变其政策初衷。选民是差异化的，他们拥有自己的政治立场，可以将选民想象成位于坐标轴$$[-1,1]$$上的均匀分布。选民总希望选择与自己政治立场接近的政党（政策）。但是由于信息的不完全，选民并不能完全确定自己的最终立场，这除了取决于选民在坐标轴上的位置，也取决于世界处于何种状态。因此，即使选民在投票之前已经知道了执政党所秉持的政策，但是由于其自身立场的不确定性，并不能明确判断哪个政党的政策更接近于自己。

<br/>

媒体是信息的唯一提供者。媒体有三种选择，推荐民主党、推荐共和党或者保持中立。例如媒体可以通过政治倾斜的方式来暗示自己支持的政党或者保持中立。媒体在知晓执政党的政策以后，制定推荐策略，即针对不同的状态制定不同的推荐。这里有两点假设，第一，媒体制定与执行策略具有一致性。即在状态实现以后，仍然要按之前制定的策略来执行。第二，媒体采用的策略是单调的，例如针对民主党，当状态小于其临界值$$z_{-1}$$时（更偏向于负端），媒体选择推荐，反之则不推荐；针对共和党，当状态大于其临界值$$z_{1}$$（更偏向于正端），媒体选择推荐，反之不推荐。

<br/>

选民在得到媒体的推荐之后进行投票。在均衡中，选民必然是知道到媒体策略方式的。因此，媒体的推荐本身就传递出了有用信息，选民据此可以判断出状态实现的区间。而这个信息也最终影响了选民对哪个政党投票。当然，选民可以消费或者不消费媒体。如果不消费媒体，则没有任何效用。而消费媒体，效用包括与政治无关的和政治相关的两部分：与政治无关的部分$$\alpha>2$$是固定的，而与政治相关的效用是这样形成的: 

1. 当选民最终发现自己的立场与A党更接近，而媒体也推荐了A党，则从消费中获得效用1；
2. 当选民最终发现自己的立场与A党更接近，而媒体推荐了B党，则从消费中获得效用$$-\beta$$，($$\beta>1$$)；
3. 当媒体选择了中立，此时无论选民最终发现离哪个党派更接近，从消费中获得的效用都为0.

由于选民自身立场的不确定性，与政治相关的效用是一个预期效用。而最终获得的净效用为固定效用+与政治相关的效用-消费媒体的价格$$q$$。当净效用大于0时，选民消费媒体；反之不消费。

<br/>

博弈的时间顺序是，

1. 政党选择政策$$p_{i}$$
2. 媒体制定推荐方案$$M$$
3. 媒体观测到状态$$s$$，根据之前的方案进行推荐
4. 选民选择消费媒体或者不消费
5. 选民进行投票，执政党产生
6. 选民知道最终状态$$s$$，最终净效用实现

在媒体垄断的情况下，子博弈均衡的结果是：均衡中，没有任何极化；媒体保持中立；所有消费者都消费媒体。即均衡为，
$$p_{-1}=p_{1}=0; z_{-1}=-\frac{1}{2},z_{1}=\frac{1}{2},q=\alpha$$， 因此，对于所有的状态$$s$$,都有$$M=0$$。
因为媒体保持中立，所以选民的净效用即为$$\alpha$$，愿意接受的价格也为$$\alpha$$；由于媒体不会透露任何有用的信息，对于中位选民来说，平均的合意点还是在原点上，因此两个政党都会选择零点，即中位选民的合意点作为自己的政策，从而来争取选举的胜利。注意这里有一点假设是，选民的偏好是单峰的，在这个假设下，中位选民的选择会决定选举的结果。

<br/>

那么为什么这时候媒体保持中立的选择也是最优的呢？

这个均衡实际上有赖于三个假设，

1. 选民的政治立场是足够差异化的，即$$[-1,1]$$的区间大于政策的选择区间$$[-\frac{1}{2},\frac{1}{2}]$$；
2. 相比媒体中立，选民更讨厌对半时间与自己的立场相佐的媒体推荐，即$$\beta>1$$；
3. 媒体的带来的固定效用要相对够大，即$$\alpha \geq 2$$。

前面两点保证了当垄断的媒体有政治偏向时，会使靠近中位值的选民效用升高，而相对远离中位值的选民效用降低；第三点保证了选民消费媒体的保留效用还是比较高的，这样垄断媒体并不想因为自己的政治偏向失去那部分相对原理中位值的市场。所以在这三个参数的假设下，垄断媒体最终选择了中立，从而减小了政党的政治极化。
  

<br/>

当引入竞争性的媒体的时候，每家媒体只能服务于坐标轴上很小的一部分。对于每一部分，媒体的政治偏向都不会太大的降低选民的效用，而选民接收到的关于状态的信息会变得更加的精确。在这种情况下，政客选择极化的政策是有利的。因为在信息被充分揭露的情况下，他们的胜选概率没有降低，同时，由于他们回到了自己最合意的政策点上面，预期效用就提高了。

### 评论

在我看来，文章的主要权衡在于，如果有政治偏向，则能向选民透露更多关于状态的有用的信息，我称为“信息效应”；但是政治偏向又会得罪一部分政治相对极端的人，我称为“感情效应”。

<br/>

在媒体有政治偏向的时候，对于在中值点附近的人，他们能利用媒体的信息提高投票的准确度，这时信息效应大于感情效应，因而会提高他们的效用。但对于远离中值点的人来说，他们政治立场比较极端，媒体的信息很难影响到他们的投票，而媒体政治偏向反而会得罪到他们。感情效用大于信息效应，因而降低了他们的效用。参数设定使得媒体并不想失去政治较为极端那部分选民的市场，因此，媒体垄断导致的均衡的结果是媒体采取中立的策略，尽量避免得罪选民。
  
<br/>

正如作者所说的，媒体究竟采取怎么样的策略，实际上还是受到选民政治极化程度，固定效用$$\alpha$$大小的设定等的影响，出于结论稳健性的考虑，作者也做了相应的讨论。
不出意外的是，当选民的政治差异度减小的时候，感情效应变得不再明显，因此，媒体会选择偏向性的推荐策略。而由于媒体的偏向性，使得在均衡中信息能够更多的传达给选民，这在一定程度上鼓励了政党的差异化。这种稳健性的讨论使得文章更加趋于严密。

<br/>

而在媒体竞争的情况下，每家媒体只能占据到很小的一块地方。这时候感情效应大大减弱了，同时信息效应变得更强了。媒体愿意选择更加具有偏向性的推荐。由于信息的充分性，选民可以最优的进行投票。政党也愿意选择极化的策略。



