目前，移动机器人在生态监测、仓库管理和极端环境探索以及家庭服务等方面都有广泛的应用，这便为机器人的设计带来了挑战，要求其能适应不同环境，在多个环境中运行

目前主流有两种机器人设计

1. 仿生设计，没有体现工程材料的优越性

2. 为每种环境都加一个机制,这是非常低效的设计

为了解决上述的问题，该论文提出了“adaptive morphogenesis”（自适应性形态发生）——一种通过统一的结构和驱动系统实现机器人形态和行为改变的设计策略。在具体的实验中，目的是在水、陆及过渡区域中实现专业化的多环境运动。



从之前的图不难发现，研究人员分别从陆龟和水龟身上获得了灵感并制作了这样一个机器人。陆龟和水龟显著的不同就是它们的腿，这也是他们能在不同环境生存、运动的原因。水龟的平蹼以及陆龟的柱型腿—>两栖机器龟(Amphibious Robotic Turtle，ART)



除了模仿两种腿的形态，更重要的是，如何实现这两种腿形态的变形，以在不同的环境使用对应的形态。实现的该机器人叫ART。

它由传统的机器人组件和刺激响应软材料组成，这使ART的四肢形状和步态的改变成为了可能，以适应多种环境的运动。这种策略便是“adaptive morphogenesis”



“adaptive morphogenesis”的解释：morphogenesis 指因适应环境而出现的形态及其产生的功能。“adaptive morphogenesis”在生物学中描述的是细菌基于环境而改变形状和大小的现象。和该研究中机器人的改变有异曲同工之妙



引出本文研究的主题“adaptive morphogenesis”后，重点来了，如何评估和得出具体有效的策略以及该策略的有效性，这里使用了COT进行量化，当然，成本越低越好。

(1)与其他动物和机器人相比，评估ART在两种环境中的运输成本(COT)，COT无量纲（单位为1），故可以在不同动物和机器人之间比较。

$$COT = \frac{P_{in}} {mgv}$$

(2)结合两种环境中的有利策略，得出二者之间的过渡策略



最后，简单介绍一下ART的具体构造，最主要的就是4个部分：一个容纳电子元件，用于控制和压舱的底盘、上下两个提供流线型结构的外壳、4个变形肢、还有含电机用于驱动的肩关节（每个肩关节含3个电机，相当于一个电机控制一个方向的转动）

ART的特点就是有这4个变形肢体，能够根据环境调整其硬度和形状，并且完全集成到机器人结构中，提高了测试的效率。

如何来实现肢体变形：像吹糖，温度和力！

变形肢具有一对拮抗的气动执行器并通过具有粘附性的热固性聚合物连接到肩关节。嵌入其中的加热器加热热固性材料使其软化，并给气动推杆充气，使肢体的硬度和大小发生变化。这些变化使ART的肢体能够在有利于陆地行走的圆柱形（leg mode）和有利于水中游泳的平蹼形（fipper mode）之间进行变换。（turn to page7）



接下来就到了实验部分，根据环境划分为水、陆、过渡区 测试

水中测试：

在水中测试时，根据ART的浮力需分为为表面和水下游泳两种情况。why？



随着四肢变形为平蹼型（flipper mode），研究者分别研究了淡水龟和半水生哺乳动物的划水（padding），以及海龟和水生哺乳的拍打（flapping）。

划水（padding）步态是一个先向后再向前和向背进行羽化恢复的动作。



拍打（flapping）步态则是由连续的上冲和下冲组成的垂直运动动作。

拍打步态与迎角θ（见图）强相关，因此，步态对应的COT也与迎角θ强相关



首先，明确一个点，就是padding（划水）的COT应该是一个值，因为它的运动步态是恒定的，而flapping因为有不同的迎角，所以会有不同的步态，即有不同的COT

分成了三个区域：

拍打比划水效率低的区域；

（划水padding的COT大约为6.2）

COT明显开始下降的区域

COT开始趋于平稳的区域

θ=$$40^\circ$$时，COT最小。



why that？解释：划水和最佳拍打（flapping）步态之间的COT差异，将ART固定在一个多轴负荷传感器上获得的向前（Fx）和向上（Fz）的方向力。

Fx的曲线表明，在划水（padding）步态的恢复（Recovery）部分产生了反作用力，导致ART明显减速或向后移动。只有27%的划水动作构成了正向推力。在拍打步态的下冲（Downstroke）过程中，ART也会减速，但在95%的冲程中保持有成效的Fx推力。

padding时的Fz峰值为3.4N，此处出现了pitching（颠簸）

因为：

阻力公式：$$F_D= \frac{1}{2} ρv^2 C_D A$$

ρ：水的密度

$$C_D$$：阻力系数

v：ART的前进速度

A：迎面气流的投影面积

越偏离x方向，A越大，故阻力也越大。书本举例。

相比较而言：flapping时，Fz峰值仅为2.5N，保持了水平的机身，故A较为恒定

结论：

任何一种步态在特定环境下都是有用的：如果要在浅水中获得较高的加速度，选paddling；如果在深水（海水）想有较为恒定的速度，选flapping。这与现实中龟的做法相同，淡水龟的padding提高了机动性；海龟的flapping提高了游泳效率。ART实现了不同环境下使用这两种不同步态的机制，保持最有利的肢体形态，加强了adaptive morphogenesis适应不同环境的能力。



陆地测试：

研究人员在瓷砖、水泥路和花岗岩为代表的室外城市环境基质上评估了陆地运动策略。

论文提出了一种静态稳定的爬行步态，这是受陆龟和其他四足动物低速直立行走的启发。当爬行时，ART每次只有一个肢体离开地面，同时逐步转动其身体向前移动。



ART的肢体在不同基质上爬行的3D动作捕捉显示了一致的扫动轨迹和步长，验证了该步态的普适有效性。



同时运动捕捉数据也帮助解释不同基质的COT差异。Z轴数据投影（z*）体现：

（1）当ART摆动腿部进行踏步阶段时的急剧增加

（2）不同地形，表现出不同的图线振动特征。例如在pivot转动或stance起步阶段时，间断性接触地面带来了ART运动的不稳定

z轴数据在步态周期中的漂移表明ART行走时腿部逐渐伸展或收拢。



只看z轴的数据，作者计算了z轴数据与理想的的轨迹（z※）的偏差，在这个过程中，ART的肢体将完全与地面接触。

![image-20221102200140204](image.png)

i表示轨迹从1-N的各点，S是稳定度，表示z轴偏离理想轨迹的程度，相当于轨迹各点偏离量的标准差

COT和S之间的正相关关系说明了与基底保持无滑动接触的重要性，与基底有关的滑动可归因于摩擦和地形特征。比如，花岗岩是相对粗糙的，有一系列的表面法线，所以它的S比相对光滑的瓷砖高64%。

结论：在不同的陆地环境下，ART适应陆地的肢体能轻易地穿越实验中的基质，说明了adaptive morphogenesis适应环境的多样性。



这引出了一个问题：该使用哪种肢体和步态来实现水陆的过渡与转换？



过渡测试：

过渡地带以流化沉淀物为主，它们会对机器人的运动产生阻力影响其稳定性。

在这一地带中的运动效率取决于屈服应力，而这个力又主要与基质深度、水占比和其中颗粒大小硬度相关



先测试了直立行走，发现不适合，在沙上爬行：超过屈服应力而滑倒然后埋进沙里，在伴水底物上爬行：结果在鹅卵石上打滑



最后，作者选择了类似于海龟在海滩上运动的爬行步态来作为在过渡基底上的运动方式。当爬行时，ART俯卧，同时四肢同时发力，并略微向上抬起，向后推获得动力向前进。这种爬行步态可以分散ART自身的重量，避免滑倒，并防止其在运动过程中被困住。通过这种爬行，ART能够成功穿越两种过渡地形，但不足是其COT值比在陆地上爬行时高出140%。



为了解释升高的COT，研究这做了基质和ART的组成材料之间进行了摩擦试验。结果显示，外壳的COT与静态摩擦系数（μ）之间呈正相关，而肢体材料的COT与μ之间呈负相关，这表明支配COT的主要因素是ART的外壳摩擦，四肢的摩擦以及机器人前部的颗粒聚集也可能影响到COT。



作者将ART在水中、陆地上和过渡基质上的运动策略结合起来，实现了一个完整地从陆地到水中的过渡路线。过渡区域由一个入海口组成，那里有坚硬的鹅卵石土壤，连接着潮湿的沙土，然后是布满岩石和植物的浅滩。ART使用腿部leg模式和直立前进creeping的方式来穿越坚硬的土壤部分。当ART接近水面时，基质吸满了水，变得湿润，它开始crawling爬行，以保证稳定性。当它在浅水区且仅部分被淹没时，它依靠划水padding来游泳。最后，当全进入水中，则是拍打flapping。



ART时刻记录着它在运动过程中的环境，其对周围环境造成的破坏很小。在性能方面，ART的最小COT与许多陆生、水生动物和机器人进行了比较。由于专门针对多种环境，ART的表现与最先进的单模态水生或陆生机器人相近，在某些情况下甚至超过了后者。最重要的是，ART可以在非单一结构化的环境中完成过渡，同时保持与单模态机器人相当甚至更好的性能。

例如，ART比terrestrial legged robots（陆地有腿机器人）如MIT的learning biped（学习双足动物)的性能好3倍，并且表现类似于unimodal tethered quadrupeds（单峰系留四足动物）(如Cheetah Cub and Titan V-III.猎豹幼崽和泰坦V-III)。ART的性能超过了许多专门的水生机器人，包括介电弹性体驱动的jellyfish机器水母10倍，single-motor-actuated fish单电机驱动的鱼2倍。



#### 小结：

在非结构化的动态环境中，例如陆地到水的过渡，作者发现将身体形状和行为视为可以调整的变量的机器人设计可以提高效率。ART结合了传统的机器人组件和龟在三种环境的运动模式，并使用了可变刚度复合材料来实现不同的形状和功能，以此减少了形态和行为方面的妥协。

但这样做出现了几个问题，如形态的过渡应该在何时何地发生，能否利用过渡中的环境干扰来提高效率，以及本文研究的步态又有多接近最佳状态？

更广泛的含义是，未来的机器人可以使用自适应形态发生来专业化，而不仅仅是一个环境，而是多个环境。



### PPT:

![幻灯片1.JPG](./jpg/幻灯片1.JPG)
![幻灯片2.JPG](./jpg/幻灯片2.JPG)
![幻灯片3.JPG](./jpg/幻灯片3.JPG)
![幻灯片4.JPG](./jpg/幻灯片4.JPG)
![幻灯片5.JPG](./jpg/幻灯片5.JPG)
![幻灯片6.JPG](./jpg/幻灯片6.JPG)
![幻灯片7.JPG](./jpg/幻灯片7.JPG)
![幻灯片8.JPG](./jpg/幻灯片8.JPG)
![幻灯片9.JPG](./jpg/幻灯片9.JPG)
![幻灯片10.JPG](./jpg/幻灯片10.JPG)
![幻灯片11.JPG](./jpg/幻灯片11.JPG)
![幻灯片12.JPG](./jpg/幻灯片12.JPG)
![幻灯片13.JPG](./jpg/幻灯片13.JPG)
![幻灯片14.JPG](./jpg/幻灯片14.JPG)
![幻灯片28.JPG](./jpg/幻灯片28.JPG)
![幻灯片29.JPG](./jpg/幻灯片29.JPG)
![幻灯片30.JPG](./jpg/幻灯片30.JPG)
![幻灯片31.JPG](./jpg/幻灯片31.JPG)
![幻灯片32.JPG](./jpg/幻灯片32.JPG)