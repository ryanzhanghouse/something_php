一个标量变量就是一个用来存储数值的命名区域。
一个数组就是一个用来存储一些列变量值的命名区域。
可以使用如下的代码创建二维数组
$products = array( array( 'Code' => 'TIR',
													'Description' => 'Tires',
													'Price' => 100 ),
									 array( 'Code' => 'OIL',
									 				'Description' => 'Oil',
									 				'Price' => 10 ),
									 array( 'Code' => 'SPK',
									 				'Description' => 'Spark Plugs',
									 				'Price' => 4 ) );
sort()函数将数组按字母升序排序
asort()函数根据数组的每个元素值进行排序
ksort()函数根据关键字排序
以上为升序，以下为降序
rsort(),arsort(),krsort()

shuffle()将数组各元素随机排序
array_reverse()函数使用一个数组做参数，返回一个内容和参数数组相同但顺序相反的数组。

explode函数的原型为
array explode(string separator, string string [, int limit])
intval()函数可以将一个字符串转化成一个整数

在数组中浏览:each(),current(),reset(),end(),next(),pos(),prev()
每个数组都有一个内部指针指向数组中的当前元素，比如reset()将返回指向数组第一个元素的指针

对数组的每一个元素应用任何函数:array_walk(),原型
bool array_walk(array arr, string func, [mixed userdata])

统计数组元素个数:count(),sizeof(),array_count_values()
将数组转换成标量变量:extract()