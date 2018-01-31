# DOM2_DOM3
DOM2和DOM3


偏移量

         这两个是一对
        offsetHeight:说白了就是垂直高度，只要在边框以内的全部算上，什么内边距啊、边框啊，以及水平的滚动条
        offsetWidth:水平宽度，只要在边框以内的全部算上，什么内边距啊、边框啊，以及水平的滚动条	

         这两个是一对
        offsetTop:举个栗子就是你桌面上的一本书，书头到桌子头的距离。
        offsetLeft:一样。


       
    offsetParent 详解
                        在又定位属性(position: relative;或absolute)的时候，
                         返回最近的父元素，没有定位属性就返回 body


       1. offsetParent定义：
            那么offsetParent就是距离该子元素最近的进行过定位的父元素（position：absolute  relative fixed)
            如果其父元素中不存在定位则offsetParent为：body元素

       2. 根据定义分别存在以下几种情况
         没有已定位的父节点，且自身position: relative的DIV元素的offsetParent为BODY
         
         没有已定位的父节点，且自身position: absolute的DIV元素的offsetParent为BODY
         
         没有已定位的父节点，且自身position: fixed的DIV元素的offsetParent为BODY
         
         没有已定位的父节点，且自身position: static的DIV元素的offsetParent为BODY
         
         拥有一个已定位的父节点，且自身position: relative的DIV元素的offsetParent为其最近被定位的祖先
         
         拥有一个已定位的父节点，且自身position: absolute的DIV元素的offsetParent为其最近被定位的祖先
         
         拥有一个已定位的父节点，且自身position: fixed的DIV元素的offsetParent为BODY
         
         拥有一个已定位的父节点，且自身position: static的DIV元素的offsetParent为其最近被定位的祖先
         
         在table之内，td与table都没有定位，且自身position: relative的DIV元素的offsetParent为BODY
         
         在table之内，td与table都没有定位，且自身position: absolute的DIV元素的offsetParent为BODY
         
         在table之内，td与table都没有定位，且自身position: fixed的DIV元素的offsetParent为BODY
         
         在table之内，td与table都没有定位，
         且自身position: static的DIV元素的offsetParent为其最近的TD、TH元素
         
         在table之内，td相对定位，且自身position: relative的DIV元素的offsetParent为其最近的TD、TH元素
         
         在table之内，td相对定位，且自身position: absolute的DIV元素的offsetParent为BODY
         
         在table之内，td相对定位，且自身position: fixed的DIV元素的offsetParent为BODY
         
         在table之内，td相对定位，且自身position: static的DIV元素的offsetParent为其最近的TD、TH元素
         
         在table之内，table相对定位，且自身position: relative的DIV元素的offsetParent为其最近的TABLE元素
         
         在table之内，table相对定位，且自身position: absolute的DIV元素的offsetParent为其最近的TABLE元素
         
         在table之内，table相对定位，且自身position: fixed的DIV元素的offsetParent为BODY
         
         在table之内，table相对定位，且自身position: static的DIV元素的offsetParent为其最近的TD、TH元素


     我们可以总结以下几条规律：

         a) position为fixed元素是没有offsetParent，但firefox统一返回body。
         b) position为absolute, relative的元素的offsetParent总是为其最近的已定位的元素,
            没有找最近的td,th元素，再没有找body。
         c) position为static的元素的offsetParent则是先找最近的td,th元素，再没有找body。
         d) body为最顶层的offsetParent。


客户区大小

      clientWidth 元素的内容及其内边距所占的空间大小(边框不算在其内)
    
      clientHeight 一样


滚动大小

         scrollHeight:获取给定对象的滚动高度。
         scrollHeight;
         scrollLeft
         scrollTop
         scrollWidth


getBoundingClientRect()


              getBoundingClientRect用于获取某个元素相对于视窗的位置集合。
              集合中有top, right, bottom, left等属性。

     https://www.cnblogs.com/Songyc/p/4458570.html
    
    
    
 遍历DOM(NodeIterator和TreeWalker的使用)
              

		如果应该访问给定的节点，那么该方法返回NodeFilter.FILTER_ACCEPT;
		如果不应该访问该节点并且其子节点也没兴趣，则返回NodeFilter.FILTER_REJECT;
		如果不应该访问该节点但仍对其子节点有兴趣，则返回NodeFilter.FILTER_SKIP。

      
      可以用document对象的createNodeIterator()方法来创建NodeIterator对象，基本形式如下：
     var iterator = document.createNodeIterator(root,whatToShow,filter,entityReferenceExpansion);
     
     
     用到的四个参数意义如下：
         1、root:从树中的哪个节点开始搜索；
         2、whatToShow:一个数值代码，代表哪些节点需要搜索；
         3、filter:NodeFilter对象，用来决定需要忽略哪些节点；
         4、entityReferenceExpansion:布尔值，表示是否需要扩展实体引用；
         
         
     whatToShow参数可以有下列这些常量或其组合的取值：
         1、NodeFilter.SHOW_ALL：搜索所有节点；
         2、NodeFilter.SHOW_ELEMENT：搜索元素节点；
         3、NodeFilter.SHOW_ATRRIBUTE：搜索特性节点；
         4、NodeFilter.SHOW_TEXT：搜索文本节点；
         5、NodeFilter.SHOW_ENTITY_REFERENCE：搜索实体引用节点；
         6、NodeFilter.SHOW_ENTITY：搜索实体节点；
         7、NodeFilter.SHOW_PROCESSING_INSTRUCTION：搜索PI节；
         8、NodeFilter.SHOW_COMMENT：搜索注释节点；
         9、NodeFilter.SHOW_DOCUMENT：搜索文档节点；
         10、NodeFilter.SHOW_DOCUMENT_TYPE：搜索文档类型节点；
         11、NodeFilter.SHOW_DOCUMENT_FRAGMENT：搜索文档碎片节节；
         12、NodeFilter.SHOW_NOTATION：搜索记号节点；

         可以使用二进制操作来组合多个值：
         var whattoshow = NodeFilter.SHOW_ELEMENT | NodeFilter.SHOW_TEXT;
         常用的有按位或运算符"|"和按位取补运算符"~";
         
         filter参数可以指定一个自定义的NodeFilter对象，但如果不想使用它的话，也可以留空（null）；
         要创建最简单的访问所有节点的NodeIterator对象，可以使用下面的代码：
         var iterator = document.createNodeIterator(document, NodeFilter.SHOW_ALL, null, false);
         
         要在搜索过程中前进或者后退，可以使用nextNode()和previousNode()方法：
         var node1 = iterator.nextNode();
         var node2 = iterator.nextNode();
         var node3 = iterator.previousNode();
         alert(node1 == node3);输出结果为“true”;
         
         
         例如，想列出某个区域内指定<div />中包含的所有元素。下列代码可以完成这个任务：
     

             <html>
                  <head>
                  <title>dom中的NodeIterator对象示例</title>
                  <script>
                  function makelist()
                  {
                     var divnode = document.getElementById("div1");

                     var iterator = document.createNodeIterator(divnode, NodeFilter.SHOW_ELEMENT, null, false);
                     var oput = document.getElementById("textarea1");
                           //nextNode指向下一个具体的节点
                     var node = iterator.nextNode();
                     while(node)
                     {
                        oput.value += node.tagName +"\n";
                        node = iterator.nextNode();
                     }
                  }
                  </script>
                  </head>
                  <body>
                  <div id="div1">
                     <p>你好<b>读者!</b></p>
                     <ul>
                        <li>列表项一</li>
                        <li>列表项二</li>
                        <li>列表项三</li>
                        <li>列表项四</li>
                     </ul>
                  </div>
                  <textarea id="textarea1" rows="10"></textarea><br />
                  <input type="button" value="生成列表" onclick="makelist()" />
                  </body>
                  </html>　





            但假设不想在结果中包含<p />元素。这就不能公用whatToShow参数来完成。
            
            这种情况下，就要用到filter参数，而filter参数需要自定义一个NodeFilter对象，
            该对象只有一个方法acceptNode()。
            如果应该访问给定的节点，那么该方法返回NodeFilter.FILTER_ACCEPT;
            如果不应该访问该节点并且其子节点也没兴趣，则返回NodeFilter.FILTER_REJECT;
            如果不应该访问该节点但仍对其子节点有兴趣，则返回NodeFilter.FILTER_SKIP。

       代码如下：
 
                  <html>
                  <head>
                  <title>dom中的NodeIterator对象示例</title>
                  <script>
                  function makelist()
                  {
                     var divnode = document.getElementById("div1");
                     var
                      FILTER= new Object();
                      FILTER.acceptNode = function(node)
                     {
                return (node.tagName == "P") ? NodeFilter.FILTER_REJECT : NodeFilter.FILTER_ACCEPT;
                     }
     var iterator = document.createNodeIterator(divnode, NodeFilter.SHOW_ELEMENT, FILTER, false);
                     var oput = document.getElementById("textarea1");
                     var node = iterator.nextNode();
                     while(node)
                     {
                        oput.value += node.tagName +"\n";
                        node = iterator.nextNode();
                     }
                  }
                  </script>
                  </head>
                  <body>
                  <div id="div1">
                     <p>你好<b>读者!</b></p>
                     <ul>
                        <li>列表项一</li>
                        <li>列表项二</li>
                        <li>列表项三</li>
                        <li>列表项四</li>
                     </ul>
                  </div>
                  <textarea id="textarea1" rows="10"></textarea><br />
                  <input type="button" value="生成列表" onclick="makelist()" />
                  </body>
                  </html>




      例子  只迭代出dom里面的所有 "li"
   
         
               <html>
                  <head>
                  <title>dom中的NodeIterator对象示例</title>
                                    <meta charset="UTF-8">
                  <script>
                  window.onload=function(){
                             var divnode = document.getElementById("div1");

                      var filter=function(node){
                            return node.tagName.toLocaleLowerCase()=="li"?                 NodeFilter.FILTER_ACCEPT:NodeFilter.FILTER_SKIP;
                      }
                      var iterator=document.createNodeIterator(divnode,NodeFilter.SHOW_ELEMENT,filter,false);

                      var node=iterator.nextNode();
                       while(node!=null){
                           console.log(node.tagName);
                        node=iterator.nextNode()	
                      }

                  }
                  </script>
                  </head>
                  <body>
                  <div id="div1">
                     <p>你好<b>读者!</b></p>
                     <ul>
                        <li>列表项一</li>
                        <li>列表项二</li>
                        <li>列表项三</li>
                        <li>列表项四</li>
                     </ul>
                  </div>

                  </body>
                  </html>




  使用TreeWalker遍历DOM树

          使用TreeWalker遍历DOM树,即使不定义过滤器,也可以取到所有 li元素,

           例子 如下

                  <html>
                  <head>
                  <title></title>
                    <meta charset="UTF-8">
                  <script>

                  window.onload=function(){
                             var divnode = document.getElementById("div1");
               var iterator=document.createTreeWalker(divnode,NodeFilter.SHOW_ELEMENT,null,false);

                        iterator.firstChild(); //转到<p>
                        iterator.nextSibling(); //转到<uL> 
                        var node=iterator.firstChild();  //转到第一个<Li>

                       while(node!=null){
                           alert(node.tagName);
                           node=iterator.nextSibling();
                       }

                  }
                  </script>
                  </head>
                  <body>
                  <div id="div1">
                     <p>你好<b>读者!</b></p>
                     <ul>
                        <li>列表项一</li>
                        <li>列表项二</li>
                        <li>列表项三</li>
                        <li>列表项四</li>
                     </ul>
                  </div>

                  </body>
                  </html>
                  
                  
         因为我们知道<li>元素在文档结构中的位置，所以可以直接定位到哪里，
	即使使用 firstChild()转到<p>元素，使用nextSibling()转到<ul>元素，
	然后在使用	firstChild()转到第一个<LI>元素。
		
	注意此处： 	TreeWalker只返回元素(由传入到createTreeWalker() 的第二个参数决定)。
	因此，可以放心使用nextSibling()访问每一个li元素，直至这个方法最后返回 null
    
                  
                  
                  
                  
                  
                  
                  
                  
