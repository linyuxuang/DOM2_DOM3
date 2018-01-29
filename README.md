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













