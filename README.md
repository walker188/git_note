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


