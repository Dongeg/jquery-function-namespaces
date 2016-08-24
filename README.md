# jquery-function-namespaces
jquery函数的命名空间用法

在jquery on()绑定 off()解除绑定方法中，给绑定或解绑的函数加一个后缀，，在后面处理时可以只对相同后缀的函数处理。<br>
<h3>举个栗子</h3>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
   <style type="text/css">
        .main{
        	width: 100px;
        	height: 100px;
        	border: 1px solid #aaa;
        	margin: 50px auto;
        }
   </style>
</head>
<body>
  <div class="main"></div>
  <script type="text/javascript" src="jquery-3.1.0.js"></script>
  <script type="text/javascript">
  	$(function(){
  		$(".main").on('mousedown',function(){
  			that=$(this)
  			$(this).css('background','green');
  			//添加命名空间后缀
  			$(window).on('mousemove.main',function(){
  				                       that.css('background','red')
  				                   })
  			        .on('mouseup.main',function(){
  			        	               console.log("mouseup")
  			        	               that.css('background','yellow')
  			        	               //解绑时使用.main后缀,这样就不会解绑window下其他的mouseover和mouseup函数
  			        	               $(window).off('.main')
  			        	           })
  		})
  	})
  </script>
</body>
</html>
```
