ajax WEB

​	展示数据 <table>中首先写好thead tbody空余 ，在html加载完之后调用ajax函数 url为拿数据的do路径  拿到数据后 拼接str  str是对data的循环 同时要用到data[i]  前后拼接<tr></str>  两端拼接<td></td> 中间写入data[i].instockId  通过innerHtml写入到tbody中

对删除按钮添加ajax事件通过class选择器  与此同时拿到url和idValue  在ajax中type为get data为idValue url为进入的servlet路径

​	删除：进入servlet中处理之后直接跳转到show页面 success中直接在iframe中写入 

​	修改：进入servlet中处理之后 success拿到数据之后load修改页面  第二参数函数中利用$(控件id)val（data.class.filed）对修改页面中的控件进行赋值 在前一个页面就可以选择到后一个页面的控件 data属性中 引号中的内容是用来req.getparameter用的 后面的值才是真实的值  进入servlet之后 通过json包装利用out写入  

  登陆过滤器(一定要调用chain中的doFilter方法)

实现filter接口 修改arg为req resp chain  转换类型为httpservlet 得到session   得到uri

判断session中的姓名是否为空以及uri是否有例外 if中调用chain的doFilter放行没有转换类型的req和resp  加上return  if外跳转到login.jsp



 

