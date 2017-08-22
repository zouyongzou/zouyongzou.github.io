---
layout:   post
title:    "JavaScript DOM 操作"
date:     2016-5-1
excerpt:  本文参考自《DOM 启蒙》一书，简单列举了常用的 DOM 操作，学习更有效率地操作HTML，而非第三方库。
tags:     [JavaScript]
---

本文参考自《DOM 启蒙》一书
{: .notice}

##### 1、节点概览
**节点属性：**  
childNodes：产生一个类数组的包含直属子节点的列表（NodeList）  
firstChild  
lastChild  
nextSibling  
previousSibling  
nodeName：节点名称  
nodeType：节点类型  
nodeValue：节点值  
parentNode：父节点

**节点方法：**  
appendChild()：附加一个（或多个）节点到调用该方法的节点的子节点的末尾。  
cloneNode()：复制单个节点或者该节点及其所有子节点。参数true或false，默认false,true（深度克隆）。在复制元素节点时，它所有的属性及其值（包括内联事件）都会被复制。任何通过addEventListener()和node.onclick方式添加的都不会被复制。可能会导致文档中有重复的id。  
compareDocumentPosition()：获取选取节点相对于传入节点的信息。返回（0、1、2、4、8、16）十六进制；对应信息为：相同、不在同一文档、传入在选取之前、传入在选取之后、传入是选取上辈、传入是选取下辈。  
contains()：知晓某个节点是否被另一个节点所包含。包含（相同）返回true。  
hasChildNodes()  
insertBefore()：两个参数：要插入的节点，和文档中要在哪个节点之前插入的该节点引用。如略点第二个参数，则行为与appendChild()无异。  
isEqualNode()：判断该节点是否与你以参数形式传入的节点相等。  
removeChild()：移除节点。先选取要移除的节点，然后获取其父节点，通常使用parentNode属性。  
replaceChild()：替换节点。

**文档方法：**  
document.createElement()：创建元素节点。该方法接受一个参数，一个指明要创建的元素类型的字符串。该字符串与Element对象tagName属性返回的字符串相同。  
document.createTextNode()：创建文本节点。

**HTML与Element属性：**  
innerHTML：获取节点内容，会将字符串中的HTML元素转换为DOM节点。  
outerHTML：获取节点内容（包括节点）。  
textContent：只会构造文本节点。提取所有文本。  
innerText：非标准扩展。  
outerText：非标准扩展。  
firstElementChild  
lastElementChild  
nextElementChild  
previousElementChild  
children：所有元素节点。  
childElementCount：计算某个节点中的子元素节点数目。

**HTML元素方法：**  
insertAdjacentHTML()：('beforebegin||afterbegin||beforeend||afterend','htmlNode')。
##### 2、文档节点
doctype  
documentElement  
implementation  
activeElement：取得文档中聚焦/激活节点的引用  
body  
head  
title：标题  
lastModified：最后修改时间  
referrer：来源  
URL：链接  
defaultview：到顶部/全局对象的捷径，即window object。  
compatMode：兼容模式  
ownerDocument：从某一元素取得文档的引用。  
hasFocus()：知道用户当前是否聚焦在加载该HTML文档的窗口上。
##### 3、元素节点
createElement()：创建元素。 
tagName：标签名。  
children  
getAttribute()  
setAttribute()  
removeAttribute()  
hasAttribute()  
classList()：获取类属性值列表。.classList.add('')&.classList.remove('')  
dataset  
attributes：获取元素属性与值的列表/集合。
##### 4、元素节点选取
querySelector()  
getElementById()  
querySelectorAll()  
getElementsByTagName()  
getElementsByClassName()  
    **预定义的元素节点选取/列表**  
document.all：HTML 文档中所有元素  
document.forms：HTML 文档中所有\<forms\>元素  
document.images：HTML 文档中所有\<img\>元素  
document.links：HTML 文档中所有\<a\>元素  
document.scripts：HTML 文档中所有\<script\>元素  
document.styleSheets：HTML 文档中所有\<link\>或者\<style\>元素  
matchesSelector()：判断一个元素是否匹配某个选择器字符串
##### 5、元素节点几何量与滚动几何量
offsetParent：offsetTop、offsetLeft  
getBoundingClientRect()：获取元素相对于视区的Top,Right,Bottom及Left边沿偏移量。以及尺寸（border+padding+content）  
offsetWidth,offsetHeight：返回元素在视区的尺寸（border+padding+content）。  
clientWidth,clientHeight：返回元素在视区的尺寸（padding+content），不含（border）。  
elementFromPoint()：获取视区中某一特定点上最顶层的元素（如无Z轴索引值，则是文档中最后一个元素）。  
scrollHeight,scrollWidth：获取滚动元素的尺寸。  
scrollTop,scrollLeft：获取并设置从上、左边滚动的距离。  
scrollIntoView()：滚动元素到视区。
##### 6、元素节点内联样式
setProperty('propertyName','value')：设置  
getPropertyValue('propertyName')：获取  
removeProperty('propertyName')：移除  
cssText：获取、设置及移除style属性的整个值（即所有内联CSS属性）。  
setAttribute('','')：设置  
getAttribute('')：获取  
removeAttribute('')：移除  
getComputedStyle：获取元素的已计算样式（即包含任何级联样式的实际样式）。
##### 7、文本节点
textContent  
splitText()：分割文本节点  
appendData()  
deleteData()  
insertData()  
replaceData()  
subStringData()  
normalize：合并兄弟文本节点成单个文本节点。  
data  
document.createTextNode()
##### 8、DocumentFragment节点
createDocumentFragment  
cloneNode()
##### 9、CSS样式表与CSS规则
disabled：使样式表失效/生效  
href  
media  
ownerNode  
parentStyleSheet  
title  
type  
cssRules：即附加到某个选择器的CSS属性与值的接口，Array[]。  
ownerRule  
deleteRule(index)  
insertRule(css规则，index)
##### 10、DOM中的JavaScript
defer将推迟外部JavaScript文件的阻塞、下载与执行，直到浏览器完成解析并关闭</html>节点。  
async可以覆盖\<script\>元素在web浏览器构造DOM时的默认的顺序、阻塞加载的天性。
##### 11、DOM事件
preventDefault()：撤销浏览器默认事件。  
stopPropagation()：终止事件流程。  
stopImmediatePropagation()：终止事件流程与相同目标上的其他事件。  