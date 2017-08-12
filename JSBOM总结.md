# JSBOM总结  
## 一、浏览器窗口宽高  
### 窗口可视宽高  
	
	document.documentElement.clientWidth
	document.documentElement.clientHeight  
### 不包括界面元素、工具栏、滚动条的窗口宽高  
	
	window.innerWidth
	window.innerHeight  
### 包括界面元素、工具栏、滚动条的窗口宽高
	
	window.outerWidth
	window.outerHeight  
## 二、屏幕宽高  
### 整体屏幕宽高  
	
	screen.width
	screen.height  
### 可用屏幕宽高  

	screen.availWidth
	screen.availHeight  
## 三、窗口距离屏幕的边距  
### 非火狐

	screenLeft
	screenTop  
只有left和top值，没有right和bottom值  
### 火狐  

	window.screenX
	window.screenY  
谷歌和Safari也适用  
***  
## 四、location  
### (1)location.hash()  
&emsp;location.hash()是个可读可写的字符串，用途是记录页面的状态  
### (2)网页重定向  
&emsp;①location.href="网页完整路径"，可读可写  
&emsp;&emsp;location.assign("网页路径")  
&emsp;&emsp;location.replace("网页路径")  
&emsp;②区别  
&emsp;&emsp;location.href和location.assign会vhansheng历史记录，可回退到前一个页面  
&emsp;&emsp;location.replace不会产生历史记录，不能回退到前一个页面  
### (3)location.reload()  
&emsp;location.reload()重新加载页面  
参数为true时表示绕过缓存，从服务器重新加载；不谢参数的话可能会从缓存中加载  
***  
## 五、history历史记录  
### (1)history.go()  
&emsp;正数意味着前进，数字是几就前进几个页面  
&emsp;负数意味着回退，数字是几就回退几个页面  
### (2)history.back()  
&emsp;相当于页面左上角的回退按钮  
***  
## 六、userAgent  
### (1)含义：是只读字符串，声明了浏览器用于HTTP请求的用户代理头的值  
### (2)判断浏览器  
&emsp;①判断火狐：** navigator.userAgent.indexOf("Firefox")!=-1 **  

&emsp;②判断谷歌：** navigator.userAgent.indexOf("Chrome")!=-1 **  

&emsp;③判断Safari：** navigator.userAgent.indexOf("Safari")!=-1 **  
因为谷歌的userAgent的内容中也含有"Safari"，所以判断浏览器类型的时候必须先判断谷歌在判断Safari  
***  
## 七、window事件  
### window.open("网址","打开方式","新窗口宽高")  
打开方式选择在当前窗口打开的话，第三个参数定义的宽高无效  
### window.close("网址")关闭窗口