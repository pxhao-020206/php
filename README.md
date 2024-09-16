# php学习笔记
函数内部调用全局变量时，需要在函数内部使用<font color="#39c5bb">global:</font>关键字；global:$’变量名’

<font color="#39c5bb">Static 作用域</font>：假设函数a内部 $x = 0;，x++; 执行三次a函数，则返回3次 0 ；加上static后 便是 0，1 ，2； <em>static：继承最后一次执行函数后函数内变量的值（个人理解）</em>

定义常量数
1. define 
Define("fruits",["a","b","c"]);
2. const
Const fruits = ["a","b","c"];

并置运算符 "." 直接在多个变量之间直接输入.即可

var_dump() 与 echo 不同的是 echo 返回变量的值；而前者返回变量数据类型和变量值。

"=="和'==='：前者是值的判断；后者在前者基础上加上对数据类型的判断

获取字符串值长度： strlen() <em>string length</em>
<mark>strlen如果要打印，需要单独的一个echo echo $a ; [enter] echo strlen($a); 这个echo 是必须的；</mark>

查找: strpos() <em>string position</em>用于字符串中查找一个字符或指定文本：
匹配：返回查找内容中第一个字符在字符串中的位置；
不匹配：FALSE； 

运算符： %：取余数；
~：二进制数取反；
Intdiv(a,b):a/b 然后向下取整;

逻辑运算：与或非异或：或“至少一个为真” 异或”有且仅有一个为真”
三元运算符?:    (a)?(b):(c) a为true，其值为b；a为false，其值为c
组合比较符：$c = $a <=> $b;
如果 $a > $b, 则 $c 的值为 1。
如果 $a == $b, 则 $c 的值为 0。
如果 $a < $b, 则 $c 的值为 -1。

if...else ; if...elseif...else; switch: 注意case和break的使用。前者后面接变量可能的值，而使用后者可以避免代码跳入下一个case中。
