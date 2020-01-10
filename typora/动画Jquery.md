$()参数的四种函数形式

- 参数为函数 调用当前页面的ready时间
- 参数选择器 返回jquery包装集
- 参数为dom元素  转换成包装集
- 参数为html代码  转换成dom元素



菜单展开

```javascript
$(".mainMenu").click(function(){	//通过类得到div			
	$(this).next().slideToggle(1);	//div后的标签展开关闭
})
```

添加样式、样式类（逗号）

```javascript
css()函数添加样式  逗号隔开
addClass("类名")
removeClass("类名")
toggle("类名")
$("td:parent").css("background-color","red");  
```

添加属性  （ 冒号和逗号）

```javascript
attr()与prop()
移除属性 removeAttr("属性名称")
var re=$(this).attr("id"); //获得标签的id属性
$(this).prop("checked",true);// 设置标签属性 checked 选中
$("img").attr({"src":"img/butterfly2-frame1.png","title":"这是一只蝴蝶"}); 
//多个属性{} 中间用‘,’和‘:’隔开

```

jquery常见函数

```javascript
val()  里面没有参数为拿到值 有参数为设置值
click() 点击
change() 变化
html()写入内容
each() 遍历包装集中的元素  可以使用this
next() 紧接着的一个同级元素
nextAll() 后面所有的同级元素
slideToggle() 收起菜单
show()显示出来
hide() 隐藏
find() 找到某个元素 
child() 在子标记中寻找
parents() 所有上层标记  括号内可以加选择器
parent() 直接父标记




prepend 向后追加子标记
$("#prependbtn").click(function(){
    var str="<tr><td>突破</td><td>右边</td></tr>"
    $("tbody").prepend(str);
})
append 向前追加子标记
$("#appendbtn").click(function(){
    var str="<tr><td>向后</td><td>添加</td></td>"
    $("tbody").append(str);
})
before 标签前面追加标记
$("#boforebtn").click(function(){
    var htmlstr="<tr><td>002</td><td>李四</td></tr>";
    $("tbody tr").before(htmlstr);
})
after 标签后面追加标记
$("#afterbtn").click(function(){
    var htmlstr="<tr><td>003</td><td>王五</td><tr>";	
    $("tbody tr").after(htmlstr);
})
empty 清空  与remove区别（移除自身）
$("#removebtn").click(function(){
    $("tbody").empty();
})
replaceWith 替换
$("#replacebtn").click(function(){
    var htmlste="<tr><td>003</td><td>王五</td><tr>";
    $("tr:last").replaceWith(htmlste);
})
wrapInner包围
$("#surroundbtn").click(function(){
    htmlstr="<u></u>";
    $("td:last").wrapInner(htmlstr);
})
```



全选(通过prop属性设置)

```javascript
$(":checkbox").change(function(){
    var tag=$(this).prop("checked");  
    $(":checkbox").prop("checked",tag);
});
```

密码强度验证

```javascript
$("[name=userPwd]").keyup(function(){
    if($("[name=userPwd]").val().length<6){
        $("span").removeClass();
        $("#weak").css({"background-color":"red"});
        $("#normal").css({"background-color":"white"});
        $("#strong").css({"background-color":"white"});
    }
    else if(!isNaN($("[name=userPwd]").val())){
        $("span").removeClass();
        $("#weak").css({"background-color":"white"});
        $("#normal").css({"background-color":"yellow"});
        $("#strong").css({"background-color":"white"});
    }
    else{
        $("span").removeClass();
        $("#weak").css({"background-color":"white"});
        $("#normal").css({"background-color":"white"});
        $("#strong").css({"background-color":"lightgreen"});
    }
    if($("[name=userPwd]").val()==""){
        $("#weak").css({"background-color":"white"});
        $("#normal").css({"background-color":"white"});
        $("#strong").css({"background-color":"white"});
    }
})
```

购物车结算

```javascript
$(function(){	//加载完成即执行
    var obj;
    function calc(){
        if($(":checkbox:checked").length>0){
            obj=$(":checkbox:checked");
        }else{
            obj=$(":checkbox");
        }
        var sum=0;

        $(obj).each(function(){  

            var expen=$(this).parents(".row").find(".price").text();
            var num=$(this).parents(".row").find("[type=number]").val();
            if(num<=0){
                $(this).prop("checked",false);
            }
            sum=sum+expen*num;
            if(sum<0){
                sum=0;
            }

        })
        $("#result").html(sum);
    }
    calc();
    $(":checkbox").change(function(){
        calc();
    })
    $("[type=number]").change(function(){

        calc();
    })

})
```

