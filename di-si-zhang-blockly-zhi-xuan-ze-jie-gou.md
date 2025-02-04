# 第四章 Blockly之选择结构

今天，我们通过一个游戏来学习选择结构，游戏的地址如下：  
 [https://blockly-games.appspot.com/bird?lang=en](https://blockly-games.appspot.com/bird?lang=en)  
 本游戏分为10关：主要游戏规则如下：  
 ①主界面是游戏的运行界面，我们需要通过控制代码来让鸟叼完虫子后回到鸟窝，并保证不撞到墙。  
 ②代码主要由选择结构和逻辑判断组成。  
 ③点击下方的Run Program按钮后程序就会执行右侧的代码。回到鸟窝后，游戏结束，顺利通关。  
 你可以先尝试着看看鸟应该怎样去运动，并如何调用代码块。稍后我们将会详细介绍关于选择结构的各种语法。  


|  1.![](.gitbook/assets/p58.png) |  2.![](.gitbook/assets/p59.png) |
| :--- | :--- |
|  3.![](.gitbook/assets/p60.png) |  4.![](.gitbook/assets/p61.png) |
|  5.![](.gitbook/assets/p62.png) |  6.![](.gitbook/assets/p63.png) |
|  7.![](.gitbook/assets/p64.png) |  8.![](.gitbook/assets/p65.png) |
|  9.![](.gitbook/assets/p66.png) |  10.![](.gitbook/assets/p67.png) |

## 4.1 关系运算符和关系表达式

 关系运算是逻辑运算中比较简单的一种，所谓的关系运算实际上就是比较运算，将两个值进行比较，从而判断比较的结果是否满足符合的条件，比如关系表达式a&gt;5，如果a为6，那么表达式成立，结果就是真，反之，如果a的值为-1，那么表达式不成立，结果就是假。

### 4.1.1关系运算符及其优先顺序

我们有如下6种关系运算符：&gt;，&lt;，≥，≤，==，!=  
 优先级次序如下：  
  （1）前四种的优先级顺序高于后两种，前四种优先级相同，后两种优先级相同。  
  （2）关系运算符的优先级低于算术运算符。  
  （3）关系运算符的优先级高于赋值运算符。  
 举几个例子：

\(1\)c &gt; a+b   c &gt; \(a+b\)  
 \(2\)a &gt; b == c   \(a &gt; b\) == c  


### 4.1.2关系表达式

关系表达式的结果有两个，如下图所示，真和假（非真）。  
 我们需要注意“=”和“==”的区别：  
 “=”表示赋值语句，比如a = 5，是把5赋值给变量a  
 “==”是逻辑判断，比如a == 5，是表示变量a的值是否和5相等，如果相等就返回真，反之返回假，我们的blockly如下图所示，逻辑判断“==”写成了“=”，是为了方便大家去理解，但实际上你要知道这两者是有区别的，细心的读者打开blockly转换到代码就会发现代码中显示的都是“==”。  


## 4.2 逻辑运算符和逻辑表达式

### 4.2.1逻辑运算符及其优先级

 逻辑运算符包括与、或、非，在我们的blockly中，如下图所示去表示分别为和、或、非。

![](.gitbook/assets/p69.png) 逻辑和，a 和 b，当且仅当a，都为真时，结果为真。  
 逻辑或，a 或 b，只要a，b中有一个为真，结果就为真。  
 逻辑非，非 a，如果a为真，则结果为假，如果a为假，那么结果为真。  
 我们用图表的形式来表示如下：  


| a | b | a and b | a or b | not a |
| :--- | :--- | :--- | :--- | :--- |
| 真 | 真 | 真 | 真 | 假 |
| 真 | 假 | 假 | 真 | 假 |
| 假 | 真 | 假 | 真 | 真 |
| 假 | 假 | 假 | 假 | 真 |

（1）非逻辑，即非在三种运算符中优先级最高。  
 （2）逻辑“和”和“或”优先级相等，低于非逻辑

### 4.2.2逻辑表达式

 逻辑表达式的值应该是真或假，下面我们一起通过一个例子来了解下逻辑表达式在选择结构中的作用：  
  我们知道在平年中2月份是28天，闰年中2月份是29天，那么怎样去区分平年和闰年呢？我们可以通过如下的流程图来进行判断：  


![](.gitbook/assets/p70.png) 闰年的条件是符合下面二者之一：  
  ①能被4整除，但不能被100整除  
  ②能被4整除，又能被400整除  
  在blockly中有两种除法，一种是普通的除法，一种是取余除法，如下图所示：  
  普通除法直接进行计算，而取余除法将是将未整除的数保留下来，只取整数部分，并没有小数部分。  
![](.gitbook/assets/p71.png)  我们用符号/来表示除法，用%来表示取余，&&表示“和”，\|\|表示“或”，！表示“非”。  
  那么闰年就可以这样来表示：  
  （year % 4 == 0 && year % 100 ！=0）\|\| year % 400 == 0  
  那么非闰年就直接在前面加一个！符号就好了  
  ！（（year % 4 == 0 && year % 100 ！=0）\|\| year % 400 == 0）  
  转化为代码就是这样：![](.gitbook/assets/p72.png)

## 4.3 条件语句-if

### 4.3.1选择结构之if语句

 Blockly中的if语句表示选择条件，如果满足条件就执行“......”语句，在if的左侧有一个设置按钮，点开后可以添加else if和else语句，表示多重判断，你可以将左侧的模块儿拖到if下面就形成了其它三种语句。

![](.gitbook/assets/p73.png)  比如这个例子：  班里面要做一个成绩统计，成绩在90分以上就输出A，在80-90分之间就输出B，80分以下输出C：  
![](.gitbook/assets/p74.png)  我们进行到这里这个程序你大致就应该明白了上面的代码究竟写的是什么内容，第一句话就是从键盘获取一个分数赋值给score这个变量，如果90![](.gitbook/assets/p75.png)![](.gitbook/assets/p76.png)

我们把刚才闰年的那个例子用编程来实现：

运行结果如下：

 是不是挺简单的呢？下面我们将前面学习的东西巩固下，并将训练的难度进行升级：  
  ①创建两个变量，并比较这两个数的大小。  
  ②创建三个变量，分别通过键盘复制，并将这三个数由小到大输出。  
 解析：  
  ①我们比较两个数的大小时，有三种情况，大于小于和等于，因此就要用到if条件语句进行两次判断，剩下的一种情况直接用else即可， “to result append text”这个语句是字符串追加的意思，就是我们不仅仅只输出一个数字，而是输出整个结果，比如2&gt;1，2=2，2&lt;3这样的结果。

输出结果如下所示：

 ②三个数比较大小时，情况就比较复杂了，还要从小到大进行输出，这就不仅仅需要进行比较了，而且还需要进行排序，这就需要了解在程序中怎样去交换两个变量，我们来举一个现实中的例子，现在我们有两杯水，我们怎样去交换这两杯水呢？

![](.gitbook/assets/p84.png) 答案是显然的，我们需要借助第三个空杯，我们把他们编号A，B，C。  
 那么交换A，B两杯水，需要以下步骤：  
  （1）把A中的水倒入C  
  （2）把B中的水倒入A  
  （3）把C中的水倒入B  
 我们的程序也是这样，交换两个变量也需要借助第三个变量，剩下的就简单了，只要两两比较就可以了，因为要从小到大输出，所以只要前者大于后者将两个数交换就可以了。![](.gitbook/assets/p85.png)![](.gitbook/assets/p86.png)

### 4.3.2选择结构的嵌套-if嵌套

 if嵌套语句实际上就是在if语句里面还有if语句，实现了嵌套，我们刚才讲的平年闰年的问题其实也可以用嵌套的方法来解决：  
  首先判断year能否被4整除，如果能被4整除，再判断能否被100整除，这时可能还不是闰年，还要再进行判断，如果能被400整除那就是闰年，不能就是平年。  


## 4.4选择结构在生活中的应用

 其实我们在平时上网的时候网页中存在着很多的选择结构，比如说登陆注册界面，我们以qq的登陆界面为例子，如下图所示：

①qq中的昵称是可以随意的，你可以和别人的昵称是相同的，所以在昵称这栏我们在后台只需要判断是否存在非法字符就可以了，如果存在非法字符就在后面显示一个小“×”，如果昵称合法，就显示一个对号“√”。

②qq中密码的判断较为复杂，它分为三个等级，每输入一个字符后程序都会对其进行判断，如下图所示，每次判断后合格的项就会打勾，而且两次密码必须是一致的，判断是在第二次输入密码确定的。

③生日、所在地这些都是需要进行选择的，我们需要在后台将所有的信息输入到选择文本中去，这样用户只要直接进行选择就可以了。  
 ④当所有的信息全部填写完成，还要进行一次大的判断，就是所有条件全部满足时，即所有条件全都为真时，就会显示注册成功，否则就会弹出必须还要填写什么必要信息。  


理解嵌套循环了么，现在我们再来回顾开篇的例子，看看你能否做出答案。参考答案如下：

|  1.![](.gitbook/assets/p91.png) |  2.![](.gitbook/assets/p92.png) |
| :--- | :--- |
|  3.![](.gitbook/assets/p93.png) |  4.![](.gitbook/assets/p94.png) |
|  5.![](.gitbook/assets/p95.png) |  6.![](.gitbook/assets/p100%20%281%29.png) |
|  7.![](.gitbook/assets/p99.png) |  8.![](.gitbook/assets/p100.png) |
|  9.![](.gitbook/assets/p97.png) |  10.![](.gitbook/assets/p98.png) |

## 课后练习

1.写出下面各逻辑表达式的值。设a=3,b=4,c=5。  
  \(1\)a+b&gt;c && b==c  
  \(2\)a \|\| b+c && b-c  
  \(3\)!\(a&gt;b\) && !c\|\|1  
  \(4\)!\(x=a\) && \(y==b\) && 0  
  \(5\)!\(a+b\)+c-1 && b+c/2  
 2.给一个不多于五位的正整数，要求：  
  \(1\)求出它是几位数；  
  \(2\)分别阀引出每一位数字；  
  \(3\)按照逆序打印出各位数字，例如原数为321，应输出123。

## 知识梳理

