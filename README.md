# DOM2_DOM3
DOM2和DOM3


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

          【1】元素自身有fixed定位，父元素不存在定位，
              则offsetParent的结果为null（firefox中为：body，其他浏览器返回为null）

          【2】元素自身无fixed定位，且父元素也不存在定位，offsetParent为<body>元素

          【3】元素自身无fixed定位，且父元素存在定位，offsetParent为离自身最近且经过定位的父元素

          【4】<body>元素的offsetParent是null







