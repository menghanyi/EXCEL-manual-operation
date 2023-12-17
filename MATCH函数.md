#! https://zhuanlan.zhihu.com/p/671851939
# EXCEL函数——MATCH、INDEX函数
![](https://pic4.zhimg.com/80/v2-263e7db752d42b178acdf88dee7b16b2.png)

# MATCH函数

MATCH函数的作用是在一个指定的单元格区域中查找某个值，并返回该值在区域中的相对位置。

MATCH函数的语法如下：

```
MATCH(lookup_value, lookup_array, [match_type])
```
- lookup_value：要查找的值。
- lookup_array：要在其中进行查找的单元格区域。
- match_type：指定匹配类型，1表示查找大于等于lookup_value的最小值，-1表示查找小于等于lookup_value的最大值，0表示查找等于lookup_value的值。

MATCH函数的返回值是一个数字，表示lookup_value在lookup_array中的相对位置。

# INDEX函数

INDEX 函数返回表格或区域中的值或值的引用（此处的教学是返回`值`）。返回表元素或数组元素的值，该元素是通过行号和列号索引选定的。

INDEX函数的语法如下：

```
INDEX(array, row_num, [column_num])
```
- array：要返回值的数组或区域。
- row_num：要从array中返回的行号。
- column_num：要从array中返回的列号。


# MATCH函数与INDEX函数的组合使用

MATCH函数与INDEX函数的组合使用，可以实现在一个指定的单元格区域中查找某个值，并返回该值在区域中的相对位置，然后再根据相对位置返回该值。

```excel
=INDEX(lookup_array,MATCH(lookup_value,lookup_array,0)) 
```
两者组合使用类似于VLOOKUP函数，但是比VLOOKUP函数更灵活，可以前后查找，也可以左右查找。

# MATCH函数与INDEX函数的组合使用实例



|序号|类型|名称|价格|
|:---|:---|:---|:---|
|1|水果|苹果|5|
|2|水果|香蕉|3|
|3|蔬菜|萝卜|2|
|4|蔬菜|白菜|1|
|5|蔬菜|黄瓜|2|
|6|水果|梨子|4|


> 1. 在上面的表格中，我们要查找“萝卜”的价格，首先要找到“萝卜”在表格中的相对位置，然后再根据相对位置返回“萝卜”的价格。

- 首先，我们要找到“萝卜”在表格中的相对位置，这里我们使用MATCH函数，MATCH函数的语法如下：

```excel
MATCH(lookup_value, lookup_array, [match_type])
MATCH("萝卜",A2:A7,0)
```

- 然后，我们再根据相对位置返回“萝卜”的价格，这里我们使用INDEX函数，INDEX函数的语法如下：

```excel
INDEX(array, row_num, [column_num])
INDEX(C2:C7,MATCH("萝卜",A2:A7,0))
```






