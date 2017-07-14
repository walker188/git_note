# git_note
成长笔记
1、'hello'+9*2+9='hello189'
string+number=string

2、splice用于删除、插入、替换元素
arrayObject.splice(index,howmany,ele1,ele2......eleX);
index:必须，为开始删除元素的索引值。
howmany：删除数组中元素的数量，必须是数字，可以为0。
ele1:规定要添加到数组中的元素。
eleX:向数组中添加的若干元素。

3、作用域问题
var elements=document.getElementsByTagName('li');
    var length=elements.length;
    var handler = function(i){
        return fucntion(){
            alert(i);
        }
    }
    for(var i=0;i<length;i++){
        elements[i].onclick= handler(i);
 }
 
4、使用object.defineProperty可向对象添加或者修改属性，
通过hasOwnProperty可判断一个对象以及其原型链上是否具有指定名称的属性，
每个对象都有prototype属性，返回对象类型原型的引用，
在原型上扩展的可枚举方法，会被for in循环出来。

5、H5新增标签：
article: 标签定义外部的内容。
aside:标签定义 article 以外的内容。a
audio:h5新增音频标签。没有高宽属性。
canvas:h5新增画布标签。
command: 定义命令按钮(未测试)
datalist：标签定义选项列表。
datalist 及其选项不会被想显示出来，它仅仅是合法的输入值列表。
details：标签用于描述文档或文档某个部分的细节。
figure：标签用于对元素进行组合。
figcaption：定义 figure 元素的标题。
footer：定义 section 或 document 的页脚。
header：定义 section 或 document 的页眉。
hgroup：用于对网页或区段（section）的标题进行组合。
keygen:标签规定用于表单的密钥对生成器字段
mark：标签定义带有记号的文本。
meter：通过min="0" max="20"的方式定义度量衡。仅用于已知最大和最小值的度量。
nav：定义document或section或article的导航。
output：定义不同的输出类型，比如脚本。
progress：定义任何类型的任务的进度。
rp:定义若浏览器不支持 ruby 元素显示的内容
rt：定义 ruby 注释的解释
ruby：定义 ruby 注释
section：标签定义文档中的节、区段。比如章节、页眉、页脚或文档中的其他部分。
source:audio和video的属性之一。为audio和video定义媒介源。
summary:为details定义标题。
time:定义日期或时间。
video：h5新增视频标签。具有高宽属性。

6、利用:after或:before伪元素进行水平是、垂直居中
eg：<div class="mask">
        <div class="dialog">
               未知宽高元素窗口水平垂直居中(拖动右下角改变宽高)"
        </div>
    </div>
    .mask{
    position: fixed;
    left: 0;
    top:0;
    height: 100%;
    width: 100%;
    text-align: center;//子元素设置inline-block使样式生效             
    background-color: rgba(200, 200, 200, .2);
  
}
.mask:after{
    content: "";
    display: inline-block;//必须,具有inline属性
    vertical-align: middle;//对其方式生效
    height: 100%;
}
.dialog{
    display: inline-block;//具有inline属性
    border: 3px solid lightblue;
}

7、word-wrap: normal|break-word;
normal	只在允许的断字点换行（浏览器保持默认处理）。
break-word	在长单词或 URL 地址内部进行换行。
white-space:nowrap;//长文本不换行,直到遇到<br>为止，inherit：从父级元素继承white-space 属性的值。

8、li超过一定长度，以省略号显示
.nowrap li{ 
   white-space:nowrap; 
   width:100px; 
   overflow:hidden; 
   text-overflow: ellipsis; 
} 

9、侧边栏宽度固定，内容区宽度自适应问题
http://jo2.org/css-auto-adapt-width/

10、call、apply总结
http://uule.iteye.com/blog/1158829

11.事件委托以及原理
将原本需要添加到每个元素节点的监听事件委托给他们的父元素来执行，原理就是事件冒泡机制。

12、websocket
WebSocket API是下一代客户端-服务器的异步通信方法。该通信取代了单个的TCP套接字，使用ws或wss协议，可用于任意的客户端和服务器程序。WebSocket目前由W3C进行标准化。WebSocket已经受到Firefox 4、Chrome 4、Opera 10.70以及Safari 5等浏览器的支持。
WebSocket API最伟大之处在于服务器和客户端可以在给定的时间范围内的任意时刻，相互推送信息。WebSocket并不限于以Ajax(或XHR)方式通信，因为Ajax技术需要客户端发起请求，而WebSocket服务器和客户端可以彼此相互推送信息；XHR受到域的限制，而WebSocket允许跨域通信。
用法：
CODE:
// 创建一个Socket实例
var socket = new WebSocket('ws://localhost:8080'); 

// 打开Socket 
socket.onopen = function(event) { 

  // 发送一个初始化消息
  socket.send('I am the client and I\'m listening!'); 

  // 监听消息
  socket.onmessage = function(event) { 
    console.log('Client received a message',event); 
  }; 

  // 监听Socket的关闭
  socket.onclose = function(event) { 
    console.log('Client notified socket has closed',event); 
  }; 

  // 关闭Socket.... 
  //socket.close() 
};

13、avascript:判断是否是数字
function isNum (n) {
    return ('number' === typeof n) ? true : 
    'object' === typeof n ? n*1 == n : 
    false;
}
这个函数的原理在于: 先直接判断typeof是number则返回true,否则判断type是不是object，是的话就判断n*1==n。n*1能强制转换成number，不过如果不是数字，转换后也只会得到NaN了，所以不会等于他自身了。
这里要插一句：任意两个NaN都是互不相等的！！
不过’1.23’*1==’1.23’，这样却是正确的，所以我们必须在typeof n === ‘object’的情况下来强制转换类型。
最后，这两种都不是则表示参数真的不是数字了。
不过，这个函数还是有bug的，因为有一种字符串，是这样的： new String(1)，这样产生的字符串，type也是object，转成数字后也能等于自身。

14、判断boolean值
""==false    //true
0==false     //true
NaN==NaN     //false
null==undefined  //true
null==null   //true
""==null     //false
null==false  //false
'null'==true  //false
undefine==false  //false
'undefined'==true  //false
" "==false(引号里有空格)  //true
[]==false    //true
{}==false    //Uncaught SyntaxError: Unexpected token ==
false=={}    //false
'0'==false   //true
true=='undefined'  //false
false=='undefined'  //false

常见的false值：

false，0，”，null,undefined
这些没什么好说的，我要说的是有几个“看起来像是false实际上不是”的东西：
空数组，空对象（也包括空函数），’ ‘（只有一个空格的字符串），’0’（只有一个0的字符串），’null’，’undefined’
上面这些，实际上都是true。
但是，如果把它们与true对等，又会得出相反的结果：
console.log(true==[]); // false
console.log(true==' '); // false
console.log(true=='0'); // false
console.log(true=='null'); // false
console.log(true=='undefined'); // false
console.log(true=={}); // false
也就是他们都不会==true，但实际上他们的确是真值。造成上面判断失败的原因，是数据类型自动转换的问题，而if()的时候，是不做转换的，所以该是真值是就是真。

可以通过如下来判断：
// 只试验一个[]，其余的自行测试
if([]){
    alert(true)
}
接下来，就列举一些常用的真假值判断:
1.判断数组是否为空
最高效的方法是判断数组是否有长度：array.length>0，或直接：if(array.length)，当他有长度时，他就不是空数组了。
2.判断对象是否为空
简单的办法是判断对象中你需要的值，如o.b == undefined，而不是直接判断对象。如果迫不得已必须直接判断对象，要使用如下的这个函数：
function isEmpty( o ) {
    for ( var p in o ) { 
        if ( o.hasOwnProperty( p ) ) { return false; }
    }
    return true;
}(效率较低)
3.判断空字符串
这个其实很简单，只是你要明白一点：你想要的空字符串，是指没有任何内容的字符串，还是即使有个空格也算是空字符串？所以你最好对字符串进行去除首尾空格的操作，然后再判断他是不是没有任何内容。
而’null’,’0’等这些字符串，基本上已经和空字符串毫无关系了，你不应该认为他们表示false。
