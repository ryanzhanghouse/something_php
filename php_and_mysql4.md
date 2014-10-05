通常在使用用户输入的字符串之前，必须对它们进行整理。
字符串整理chop(),ltrim(),trim()
整理字符串的第一步是清理字符串中的多余的空格，PHP提供了3个非常有用的函数
trim()函数可以出去字符串开始位置和结束位置的空格，并返回结果字符串。
PHP具有一系列可供使用的函数来重新格式化字符串。
使用HTML格式化:nl2br()函数
nl2br()函数将字符串作为输入参数
使用printf(),sprintf()可以实现一些更复杂的格式
printf()函数将一个格式化的字符串输入到浏览器中，而sprintf()函数返回一个格式化的字符串
格式化字符串以便存储:addslashes(),stripslashes()

gpc表示GET,POST,cookie
explode(),implode(),join()
与explode()每次都讲一个字符串全部分割成若干小块不同，strtok()函数一次只从字符串中取出一些片段（称为令牌）
字符串排序:strcmp(),strcasecmp(),strnatcmp()
在字符串中查找字符串:strstr(),strchr(),strrchr(),stristr()
查找字符串位置:strpos(),strrpos()
替换子字符串:str_replace(),substr_replace()

PHP支持两种风格的正则表达式语法:POSIX,Perl，这里我们使用更简单地POSIX风格。
POSIX正则表达式更容易掌握，但不是二进制安全的

查找子字符串是正则表达式的主要应用，在PHP中，可以使用的比起用于匹配POSIX风格正则表达式的两个函数式ereg(),eregi()
ereg()原型
int ereg(string pattern, string search, array [matches]);
搜索字符串search，在pattern中寻找与正则表达式相匹配的字符串，如果找到则存储在数组matches中。
用正则表达式替换子字符串ereg_replace(),eregi_replace()
string ereg_replace(string pattern, string replacement, string search);
使用正则表达式分割字符串 split()
array split(string pattern, string search[, int max]);
