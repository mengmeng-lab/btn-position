# btn-position
底部固定按钮以及在移动端input输入框的键盘顶上去的问题
一.固定底部按钮
方案一：绝对定位
优点：兼容性较好，可以使用任何场景（推荐）
方案三：fixed定位
优点：实现简单，缺点：ios8等一些浏览器上会有跳动。
方案三：flex
优点：实现简单，缺点：较低版本浏览器对flex不支持。
二.移动端input输入框的键盘顶上去
1.原生js解决方法：
var h = document.body.scrollHeight;
    window.onresize = function(){
        if (document.body.scrollHeight < h) {
            document.getElementsByTagName("nav")[0].style.display = "none";
        }else{
            document.getElementsByTagName("nav")[0].style.display = "block";
        }
    };
2.jquery的写法：
 var h=$(window).height();
    $(window).resize(function() {
       if($(window).height()<h){
           $('.footer').hide();
        }else{
           $('.footer').show();
        }
     }     
3.另外一种情况出现在了苹果手机上，底部的input的框会被下面弹起的键盘遮住
<script type="text/javascript">
    $("input").on("click", function() {
        setTimeout(function(){ 
            document.body.scrollTop = document.body.scrollHeight; 
        },300); 
    })
</script>
