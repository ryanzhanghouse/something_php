在PHP中写文件比较简单，可以使用fwrite()或者fputs()
fwrite($fp, $outputstring);
这个函数告诉PHP将保存在$outputstring中的字符串写入到$fp指向的文件中。
fwrite()函数的一个替换函数是file_put_contents()，其函数原型为
int file_put_contents(string filename,
											string data)
这个函数可以在不需要调用fopen()函数打开要写的文件以前，将包含在data中的字符串数据写入到filename所指定的文件中。
fwrite()的原型如下：
int fwrite(resource handle, string string [, int length])
可以通过PHP内置的strlen()函数获得字符串的长度
fwrite($fp, $outputstring, strlen($outputstring));

调用fclose()函数关闭文件
fclose($fp);
如果文件被成功地关闭，函数将返回一个true值。反之，该函数将返回false

读取整个文件:readfile()
读取一个字符:fgetc()
读取任意长度:fread()
查看文件是否存在:file_exists()
确定文件大小:filesize()
nl2br()函数将输出的\n字符转换成HTML的换行符<br/>
删除一个文件:unlink()
在文件中定位:rewind(),fseed(),ftell()

flock()函数原型如下：
bool flock (resource fp, itt operation [, int & wouldblock ])

LOCK_SE				读操作锁定。这意味着文件可以共享，其他人可以读该文件
LOCK_EX				写操作锁定。这是互斥的。该文件不能被共享
LOCK_UN				释放已有的锁定
LOCK_NB				防止在请求加锁时发生阻塞

如果有两个脚本同时申请对一个文件加锁，这将导致竞争条件的问题，这连个进程将竞争加锁，RDBMS有内置的处理并发访问的机制。
如果简单考虑，可以使用PHP的SQLite扩展，这个扩展对普通文件提供了一个基本的SQL接口

使用fopen()打开文件
$fp = fopen( "$DOCUMENT_ROOT/../orders/orders.txt ", 'w');
这里使用了PHP内置变量$_SERVER['DOCUMENT_ROOT']
这个变量指向了Web服务器文档树的跟。我们使用..表示文档根目录的父目录。处于安全的考虑，这个目录位于整个文档树外部
在这个例子中，除了通过我们提供的接口，我们不希望还有其他web接口能够访问它，这个路径称为相对路径
因为它描述了一个相对于文档根目录的文件系统位置
由于我们为表单变量定义了一个简短名称，我们需要在脚本的开始处加上如下代码：
$DOCUMENT_ROOT = $_SERVER[]
我们还可以指定文件的绝对路径。这个路径是从根目录开始的（在UNIX系统中，根目录是/，而在Windows系统中通常c:\
在UNIX系统中，根目录就是/home/book/orders
这样做的问题在于，如果将网站安装到别人的服务器上，这个绝对路径可能会改变
如果系统管理员没有发出任何通知就修改目录结构，我们就不得不手工更改包含在大量脚本中的绝对路径
如果没有指定路径，这个文件就将在脚本自身所在的相同目录中查找或者创建。如果通过某种CGI封装程序来运行PHP，这可能又会有所不同，具体需要更具服务器的设置而定。
在UNIX环境下，目录中的间隔符是正斜线/。如果使用Windows平台，要使用反斜线的话，就必须使用转义（escape，标注为一个特殊字符）字符。
这样fopen()函数才能正确理解这些字符
在PHP代码中，只有少数人会使用反斜线，因为这意味着代码只能在Windows上运行。
特殊文件操作模式
b   二进制   二进制模式，用于与其他模式进行连接。如果文件系统能够区分二进制文件和文本文件，你可能会使用它，UNIX不能区分，是默认模式
$fp = fopen( "$DOCUMENT_ROOT/../orders/orders.txt", 'ab');
fopen()函数的第3个参数是可选的。如果要在include_path（在PHP的配置中设置，参阅附录A）
如果希望PHP搜索include_path，就不需要提供目录名称或路径
$fp = fopen( 'orders.txt', 'ab', true);
第4个参数也是可选的。fopen()函数允许文件名称以协议名称开始(http://)并且在一个远程的位置打开文件。
如果fopen()成功地打开一个文件，该函数将返回一个指向这个文件的文件指针
文件指针被保存在$fp中

通过FTP或HTTP打开文件
除了打开一个本地文件进行读写操作之外，也可以使用fopen()函数通过FTP、HTTP或其他协议来打开文件。
在php.ini文件中，可以通过关闭allow_url_fopen指令来禁用这个功能。
如果使用的文件名是以ftp://开始的，fopen()函数将建立一个连接到指定服务器的被动模式，并返回一个指向文件开始的指针。
如果使用的文件名是以http://开始的，fopen()函数将建立一个到指定服务器的HTTP连接，并返回一个指向HTTP响应的指针
当打开文件时，可能经常遇到的错误没有读写权限
输入如下命令，可以创建一个全局可写的目录来存储订单
mkdir ~/orders
chmod 777 ~/orders
如果fopen()函数调用失败，函数将返回false。可以以一种对应用户友好的方式来处理这个错误，可以通过抑制PHP的错误信息并且根据自己的方式给出错误信息
@ $fp = fopen( "$DOCUMENT_ROOT/../orders/orders.txt", 'ab');
if (!$fp){
	echo "<p><strong> Your order could not be processed at this time.'
				.Please try again later.</strong></p></body></html>";
	exit;
}

