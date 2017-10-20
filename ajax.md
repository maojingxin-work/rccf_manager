###Ajax原理

* 什么是ajax
    *  AJAX全称为“Asynchronous JavaScript and XML”
        （异步JavaScript和XML），
        是一种创建交互式网页应用的网页开发技术
    *   使用XMLHttpRequest对象与Web服务器进行异步数据通信
    *   使用Javascript操作Document Object Model进行动态显示及交互
    *   使用JavaScript绑定和处理所有数据
*   AJAX的工作原理
    *   Ajax的工作原理相当于在用户和服务器之间加了—个中间层(AJAX引擎),
        使用户操作与服务器响应异步化。
        并不是所有的用户请求都提交给服务器,
        像—些数据验证和数据处理等都交给Ajax引擎自己来做, 
        只有确定需要从服务器读取新数据时,再由Ajax引擎代为向服务器提交请求。
    *   Ajax其核心有JavaScript、XMLHTTPRequest、DOM对象组成，
        通过XmlHttpRequest对象来向服务器发异步请求，从服务器获得数据，
        然后用JavaScript来操作DOM而更新页面。
        *   XMLHTTPRequest对象
        *   JavaScript
        *   DOM Document Object Model
        *   XML
        *   综合
            >Ajax引擎，实际上是一个比较复杂的JavaScript应用程序，用来处理用户请求，读写服务器和更改DOM内容。JavaScript的Ajax引擎读取信息，并且互动地重写DOM，这使网页能无缝化重构，也就是在页面已经下载完毕后改变页面内容，这是我们一直在通过JavaScript和DOM在广泛使用的方法，但要使网页真正动态起来，不仅要内部的互动，还需要从外部获取数据，在以前，我们是让用户来输入数据并通过DOM来改变网页内容的，但现在，XMLHTTPRequest，可以让我们在不重载页面的情况下读写服务器上的数据，使用户的输入达到最少。
            
*   简单的ajax请求
   >   <code>
            var XHR=null;  
            if (window.XMLHttpRequest) {  
                // 非IE内核  
                XHR = new XMLHttpRequest();  
            } else if (window.ActiveXObject) {  
                // IE内核,这里早期IE的版本写法不同,具体可以查询下  
                XHR = new ActiveXObject("Microsoft.XMLHTTP");  
            } else {  
                XHR = null;  
            }  
            if(XHR){  
                XHR.open("GET", "ajaxServer.action");  
              
                XHR.onreadystatechange = function () {  
                    // readyState值说明  
                    // 0,初始化,XHR对象已经创建,还未执行open  
                    // 1,载入,已经调用open方法,但是还没发送请求  
                    // 2,载入完成,请求已经发送完成  
                    // 3,交互,可以接收到部分数据  
              
                    // status值说明  
                    // 200:成功  
                    // 404:没有发现文件、查询或URl  
                    // 500:服务器产生内部错误  
                    if (XHR.readyState == 4 && XHR.status == 200) {  
                        // 这里可以对返回的内容做处理  
                        // 一般会返回JSON或XML数据格式  
                        console.log(XHR.responseText);  
                        // 主动释放,JS本身也会回收的  
                        XHR = null;  
                    }  
                };  
                XHR.send();  
            }  
        </code>