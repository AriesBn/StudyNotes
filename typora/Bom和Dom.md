###### 函数

```javascript
var img=document.createElement("IMG"); //得到某个元素
location.href="abc.html";
window.location.reload 窗口地址栏重载



//设置属性
img.getAttribute("width") //得到原来的宽  得到的值是字符串形式的  因此要用parseInt方法
img.setAttribute("id","img1");	//设置属性
img.setAttribute("src","../../7_29/倒计时图片/plus.png");//设置属性
```

dom节点

```javascript
firstChild //第一个子节点
lastChild //最后一个子节点
parentNode //父节点
previousSibling //兄弟节点向前
nextSibling //兄弟节点向后
nodeName //节点名字
nodeType //节点类型 1 标签  2属性 3文字节点
nodeValue //文本内容
document.createElement("tr") //创建节点
appendChild() //添加节点
var trElement=tableElement.firstChild.firstChild;//得到子元素的第一个子元素
```

event

```javascript
event.clientX //获取事件发生时鼠标的X位置
event.clientY// 获取事件发生时鼠标的Y位置

```

```javascript
screen.availHeight //屏幕的高度
screen.availWidth //屏幕的宽度 都是数值
定时函数的设置与停止
var clock=setInterval("函数",1000)
clearInterval(clock);
window.history.forward() //向前进的函数
window.history.back()//向后退的函数 放在事件中
window.confirm() //是否确认，返回true或者false
```

得到图片并删除

```javascript
var imgs=document.getElementsByTagName("IMG"); //得到所有的图片元素
while(imgs.length>0){	   
    imgs[0].parentNode.removeChild(imgs[0]);   //第一个图片节点的父节点来删除它 总不能自己删除自己吧
    imgs=document.getElementsByName("IMG");	 //再次得到所有的图片节点
}	
```

清楚空白节点

```javascript
function cleanWhiteSpaceNode(element){
    for ( var i = 0; i < element.childNodes.length; i++) {
        var el=element.childNodes[i];
        if(el.nodeType==3&&/\s/.test(el.nodeValue)){// 包括空格、换行、tab缩进等所有的空白
            element.removeChild(el);
        }
    }
}
```

事件

1. oumousedown 鼠标落下
2. onmouseup 鼠标弹起
3. onmouseover 悬浮
4. onmouseout 离开

##### 选择城市关键点：

```html
var temp=document.getElementById("citySelect");   //得到select
	temp.options.length=1;							//select的options 是个数组有长度
	for(var i=0;i<citys.length;i++){				 
		temp.options.add(new Option(citys[i],citys[i]));			
	} //citys是给定的每个省份的城市//select的options数组添加元素 每个元素为一个新的option,包括value 和 两个option之间的内容
```

倒计时

```html
setTimeout("函数"，1000)
```

悬浮即离开

```javascript
function change(){
    var h=Math.random()*700;
    var w=Math.random()*1400;
    document.getElementById("div1").style.top=h+"px";
    document.getElementById("div1").style.left=w+"px";
}
```

```html
<div id="div1" onmouseover="change()" style="position: absolute; left: 10px; top: 10px;">
```

alert之后的事件

```javascript
.focus() //聚焦 用于输入框
.select()//选中  用于选中密码 
.checked() //返回true&false 表示某个控件是否被选中
```

阻止form表单提交

```html
<input type="submit" value="注册" onclick="return checkData();" />  
```

```javascript
function checkData(){
    if(regForm.userName.value==""){
        alert("用户名不能为空");
        return false; //前后呼应 return false 然后 onclick处return checked()函数
    }
}
```

修改

```javascript
document.getElementById("weak").style.backgroundColor="red"; //修改背景颜色
document.getElementById("img1").src=imgs[index];	//修改图片

```

数组

```javascript
var myArray=new Array(1,2,3,14,5,5,6);//类似与增强for循环寻找最大值
for(var i in myArray){
    if(max<myArray[i]){
        max=myArray[i];
    }
}
```

跑马灯

```html
<marquee direction="down" height="1000px" onmouseover="this.stop()"onmouseout="this.start()">//this 在这里就指代的是marquee stop停止函数 start开始函数 都是定义好的。
```

onchange用于背景选择

```javascript
document.body.bgColor="darkgreen" //直接的背颜色设置 
```

匿名函数的使用

```javascript
var a=function(){
    alert("我是匿名的函数")
}
a(); //这个时候a就指代的是funtion函数 要记得加()
```

span颜色的设置

```javascript
document.getElementById("span1").style.color="green";
```

