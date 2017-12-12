
*HTTP基础：URL格式、 HTTP请求、响应、消息
*HTTP URL
　　格式：

　　http://host[:port][abs_path]

　　其中http表示要通过HTTP协议来定位网络资源。

　　host表示合法的Internet主机域名或IP地址（以点分十进制格式表示）；

　　port用于指定一个端口号，拥有被请求资源的服务器主机监听该端口的TCP连接。

　　如果port是空，则使用缺省的端口80。当服务器的端口不是80的时候，需要显式指定端口号。

　　abs_path指定请求资源的URI(Uniform Resource Identifier，统一资源定位符)，如果URL中没有给出abs_path，那么当它作为请求URI时，必须以“/”的形式给出。通常这个工作浏览器就帮我们完成了。

 

　　浏览器与服务器连接的一般过程：

　　（以sohu网站为例）：

 

                         

URL与URI
　　URI纯粹是一个符号结构，用于指定构成Web资源的字符串的各个不同部分。

　　URL是一种特殊类型的URI，它包含了用于查找某个资源的足够的信息。

　　其他的URI，例如:mailto:zhanglong217@yahoo.com.cn，则不属于URL，因为它里面不存在根据该标识符来查找的任何数据。这种URI称为URN(通用资源名)。

 

HTTP请求
　　客户端通过发送HTTP请求向服务器请求对资源的访问。

　　HTTP请求由三部分组成，分别是：请求行，消息报头，请求正文。

　　请求行以一个方法符号开头，后面跟着请求URI和协议的版本，以CRLF作为结尾。

　　请求行以空格分隔。除了作为结尾的CRLF外，不允许出现单独的CR或LF字符，格式如下：

　　Method Request-URI HTTP-Version CRLF

　　Method表示请求的方法，Request-URI是一个统一资源标识符，标识了要请求的资源，HTTP-Version表示请求的HTTP协议版本，CRLF表示回车换行。

 

　　例如：

　　GET /test.html HTTP/1.1 (CRLF)

 

HTTP请求方法
 

GET方法

　　GET方法用于获取由Request-URI所标识的资源的信息，常见形式是：

　　GET Request-URI HTTP/1.1

　　当我们通过在浏览器的地址栏中直接输入网址的方式去访问网页的时候，浏览器采用的就是GET方法向服务器获取资源。

 

POST方法

　　POST方法用于想服务器发送请求，这点和GET方法没有区别。但是POST方法要求服务器接收附在请求后面的数据。

　　POST方法在表单提交的时候用的最多。

　　采用POST方法提交表单的例子

　　POST /login.jsp HTTP/1.1 (CRLF)

　　Accept: image/gif (CRLF) (…)

　　Host: www.sample.com (CRLF) (…)

　　…

　　Cache-Control: no-cache (CRLF)

　　(CRLF)

　　username=hello&password=123456

　　当我们在HTML中提交表单时，浏览器会根据你的提交方法是get还是post，采用相应的在HTTP协议中的GET或POST方法，向服务器发出请求。

　　注意，在HTML文档中，书写get和post，不区分大小写，但HTTP协议中的GET和POST只能是大写形式。

 

HEAD方法

　　HEAD方法与GET方法几乎是一样的，它们的区别在于HEAD方法只是请求消息报头，而不是完整的内容。

　　对于HEAD请求的回应部分来说，它的HTTP头部中包含的信息与通过GET请求所得到的信息是相同的。

　　利用这个方法，不必传输整个资源的内容，就可以得到Request-URI所标识的资源的信息。

　　这个方法通常用于测试超链接的有效性，是否可以访问，以及最近是否更新等。

 

HTTP响应
　　在接收和解释请求消息后，服务器会返回一个HTTP响应消息。

　　与HTTP请求类似，HTTP响应也是由三个部分组成，分别是：状态行，消息报头，相应正文。

　　状态行由协议版本，数字形式的状态代码，相应的状态描述组成，各元素之间以空格分隔，除了结尾的CRLF(回车换行)序列外，不允许出现CR或LF字符。格式如下：

　　HTTP-Version Status-Code Reason-Phrase CRLF

　　HTTP-Version表示服务器HTTP协议的版本，Status-Code表示服务器发回的响应代码，Reason-Phrase表示状态代码的文本描述，CRLF表示回车换行。

　　例如：

　　HTTP/1.1 200 OK (CRLF)

 

HTTP响应——状态代码与状态描述
　　状态代码由三位数字组成，表示请求是否被理解或被满足，状态描述给出了关于状态代码的简短文本描述。

　　状态代码的第一个数字定义了响应的类别，后面两个数字没有具体的分类。

 

　　第一个数字有五种可能的取值：

　　1xx：指示信息——表示请求已接收，继续处理

　　2xx：成功——表示请求已经被成功接收，理解，接受

　　3xx：重定向——要完成请求必须进行更进一步的操作

　　4xx：客户端错误——请求有语法错误或请求无法实现

　　5xx：服务器端错误——服务器未能实现合法的请求

　　如：

 


 

　　状态行由协议版本，数字形式的状态代码，相应的状态描述组成，各元素之间以空格分隔，除了结尾的CRLF（回车换行）序列外，不允许出现CR或LF字符。格式如下：

　　HTTP-Version Status-Code Reason-Phrase CRLF

 
HTTP消息
　　HTTP消息由客户端到服务器的请求和服务器到客户端的响应组成。

　　请求消息和响应消息都是由开始行，消息报头（可选），空行（只有CRLF的行），消息正文（可选）组成。

　　对于请求消息，开始行就是请求行，对于相应消息，开始行就是状态行。

　　实验工具：Telnet

　　HTTP协议与TELNET协议都是基于TCP协议。
