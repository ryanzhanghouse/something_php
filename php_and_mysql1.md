可以调用exit来终止PHP的执行，而不会执行剩下的脚本

可以调用一个函数来实现转换变量数据类型的目的
int intval(mixed var [, int base]);
float floatval(mixed var);
string strval(mixed var);

PHP有几个函数可以用来测试变量的状态，第一个函数就是isset()，函数原型为
bool isset(mixed var);
也可以传递一个由逗号间隔的变量列表，如果所有变量都被设置了，isset()函数将返回true
unset()函数销毁一个变量
void unset(mixed var);
函数empty()可以用来检查一个变量是否存在，以及它的值是否为非空和非0
bool empty(mixed var);

PHP6项基本的作用域规则
内置超级全局变量可以在脚本的任何地方使用和可见
常量，一旦被声明，将可以在全局可见，也就是说，他们可以在函数内外使用。
在一个脚本中声明的全局变量在整个脚本中是可见的，但不是在函数内部
函数内部创建并声明为静态的变量无法在函数外部可见，但是在函数多次执行过程中保持该值

我们已经提到了两个操作符：赋值操作符= 和字符串连接操作符.PHP中有类似JS的===操作符
逗号操作符,用来分隔函数参数和其他列表项
两个特殊操作符new和->，他们分别用来初始化类的实例和访问类的成员
错误抑制操作符@，可以用来在任何表达式前面使用，如果通过这种方法抑制了一些警告，一旦遇到一个警告，就要写一些错误处理代码
如果已经启用了PHP配置文件中的track_errors特性，错误信息将会被保存在全局变量$php_errormsg中
执行操作符实际上是一对操作符，它是一对反向单引号(``)
PHP将试着将反向单引号之间的命令当做服务器端的命令行来执行。表达式的值就是命令的执行结果。
$out = `ls -la`;
echo '<pre> '.$out. '</pre> ';
print和echo都不是真正的函数，但是都可以用带有参数的函数形式进行调研
print要比echo的速度慢

大部分可变函数都是用来测试一个函数的类型的，PHP中有两个最常见的函数，分别是gettype()和settype()，函数原型为
string gettype(mixed var);
bool settype(mixed var, string type);

第3中制定字符串的方法：heredoc语法(<<<)
echo <<<theEnd
  line 1
  line 2
  line 3
theEnd
Heredoc字符串是插补的，就像双引号字符串
标识符是变量的名称，PHP的特性之一就是它不需要在使用变量之前声明变量，当第一次给一个变量赋值时，你才创建了这个变量。

PHP支持如下所示的基本数据类型：
Integer用来表示整数
Float用来表示所有实数
String用来表示字符串
Boolean用来表示true或false
Array用来保存具有相同类型的多个数据项
Object用来保存类的实例
此外还有两个特殊的类型：NULL（空）和resource（资源）   特定的内置函数（例如数据库函数）将返回resource类型的变量，他们都代表外部资源（例如数据库连接）
基本是不能直接操作一个resource变量，但是通常他们都将被函数返回，且必须作为参数传递给其他函数
PHP有许多预定义常量，运行phpinfo()函数
这个函数将给出一个PHP预定义常量和变量的列表
常量只可以保存布尔值，整数，浮点数或字符串数据，这些都是标量数据。

如果表单是通过POST方法提交的，tireqty文本输入框中的数据将保存在$_POST['trieqty']中。
如果表单是通过GET方法提交的，数据将保存在$_GET['trieqty']中。
在任何一种情况下，数据都可以通过$_REQUEST['trieqty']获得。

PHP超级全局变量
$GLOBALS所有全局变量数组（就像global关键字，这将允许在一个函数内部访问全局变量----例如，以$GLOBALS['myvariable']的形式）
$_SERVER,服务器环境变量数组
$_GET,通过GET方法传递给该脚本的变量数组
$_POST,通过POST方法传递给该脚本的变量数组
$_COOKIE,cookie变量数组
$_FILES,与文件上传相关的变量数组
$_ENV,环境变量数组
$_REQUEST,所有用户输入的变量数组，包括$_GET,%_POST和$_COOKIE所包含的输入内容
$_SESSION,会话变量数组

类型操作符：instanceof

PHP还提供了一些特定类型的测试函数。每一个函数都使用一个变量作为其参数，并且返回true或false。
is_array():检查变量是否是数组
is_double(),is_float(),is_real():检查变量是否是浮点数
is_long(),is_int(),is_integer():检查变量是否是整数
is_string():检查变量是否是字符串
is_bool():检查变量是否是布尔值
is_object():检查变量是否是一个对象
is_resource():检查变量是否是一个资源
is_null():检查变量是否是null
is_scalar():检查该变量是否是标量，即，一个整数、布尔值、字符串或浮点数
is_numeric():检查该变量是否是任何类型的数字或数字字符串
is_callable():检查该变量是否是有效的函数名称
