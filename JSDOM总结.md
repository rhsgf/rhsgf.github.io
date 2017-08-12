# JSDOM总结  
## 一、节点  
### 1.类型  
(1)层级划分  
父节点，子节点，兄弟节点   
(2)类型划分  
元素节点，属性节点，文本节点，注释节点，document节点   
(3)查看方法  
①查看节点类型用nodeType：  
元素节点值为1  
属性节点值为2  
文本节点值为3  
注释节点值为8  
document节点值为9  
②查看元素节点和属性节点的名称用nodeName(注释节点的值为comment)  
③查看属性节点的属性值用nodeValue  
***  
### 2.节点关系  
(1)子节点  
①children获取指定元素的第一层子元素(所有类型是标签的子节点)  
②childNodes获取指定元素的第一层子节点(所有的子节点，包括空白空行文本)  
③firstElementChild/firstChild获取指定元素的第一个子元素(后者会解析空白文本节点)  
④lastElementChild/lastChild获取指定元素的最后一个子元素(后者会解析空白文本节点)  
(2)父节点  
①parentNode获取指定元素的父节点  
②offsetParent获取离指定元素最近的具有定位属性的父节点(没有定位父级的获取到的是body)  
(3)兄弟节点  
①nextElementSibling/nextSibling获取指定元素的下一个兄弟元素(后者会解析空白文本节点)  
②previousElementSibling/previousSibling获取指定元素的上一个兄弟元素(后者会解析空白文本节点)  
***  
### 3.节点操作  
(1)document.createElement创建节点  
(2)document.appendChild给指定元素追加子节点(只能在最后)  
(3)insertBefore(插入的元素，参照元素)插入元素  
(4)removeChild移除子节点  
(5)replaceChild(替换元素，被替换元素)替换子节点  
(6)cloneNode(Boolean)克隆节点  
①true时克隆本身及后代  
②false时只克隆本身(默认)  
(7)hasChildNodes判断指定元素是否具有子节点，返回布尔值  
***  
## 二、元素属性的方法  
(1)获取  
①元素.属性名和元素["属性名"]这两种形式获取不到非标准属性  
②getAttribute("属性名")，可以获取到元素的自定义属性  
(2)设置  
setAttribute("属性名","属性值")可以设置属性  
(3)移除  
removeAttribute("属性名")可以移除属性  
***  
## 三、图片对象事件  
(1)onload，图片加载成功时触发  
(2)onerror，图片加载失败时触发  
(3)onabort，当用户放弃加载时触发