#! https://zhuanlan.zhihu.com/p/671332231
# EXCEL函数——VLOOKUP函数

# 1. VLOOKUP函数的使用场景
VLOOKUP 是 Excel 中使用最广泛的函数之一（也是我最常用的工具之一！）。使用 VLOOKUP，你可查找左侧列中的值，如果找到匹配项，则会在右侧的另一列中返回信息。
VLOOKUP函数的语法如下：
```excel
VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])
=VLOOKUP(要查找的内容、要查找的位置、包含要返回的值的范围内的列号、返回表示为 1/TRUE 或 0/FALSE 的近似或精确匹配项)。
```
![vlookup函数参数含义](https://pic4.zhimg.com/80/v2-08c91ff41264084849886b91b5632111.png)

# 2. VLOOKUP函数的参数
VLOOKUP 函数有四个参数：
- lookup_value：要在第一列中查找的值。
- table_array：要在其中进行搜索的单元格区域，其中包含查找值和返回值。（注意：这个区域必须包含查找值。若需要锁定区域，可使用 F4 键。可按 F4 键切换绝对引用和相对引用。）
- col_index_num：要返回的值所在的列。例如，第一列为 1，第二列为 2，依此类推。
- range_lookup：可选。如果为 TRUE 或省略，则 VLOOKUP 将在查找范围内搜索近似匹配项。如果为 FALSE，则 VLOOKUP 将仅查找完全匹配项。

# 3. VLOOKUP函数的使用范例
VLOOKUP 函数最常用的用途是查找表格中的值。例如，你可以使用 VLOOKUP 函数查找产品名称，然后返回产品价格。
```excel
=VLOOKUP(C22,$C$17:$D$20,2,FALSE)
```
![测试使用](https://pic4.zhimg.com/80/v2-aacc209a6866c4d7480e0d2ffeb55470.png)

# 4. VLOOKUP函数使用过程中的注意事项
- VLOOKUP 函数如果第四个参数为 FALSE，则为精确匹配，，如果查找不到，则返回 #N/A。
- VLOOKUP 函数如果第四个参数为 TRUE，则为模糊匹配，如果查找不到，则返回最接近的值。
- VLOOKUP 函数如果第四个参数不填，则默认为 TRUE。

无一例外，你会遇到 VLOOKUP 找不到所需内容，并且返回错误 (#N/A) 的情况。有时是单纯的因为查找值不存在，或者因为引用单元格尚无任何值。

> 1.如果你知道查找值存在，但查找单元格为空，你希望隐藏错误，可以使用 IF 语句。在这种情况下，我们将使用嵌套现有 VLOOKUP 公式：
```excel
=IF(单元格="","",VLOOKUP(C43,C37:D41,2,FALSE))
```
表示如果单元格为空，则返回空白，否则返回 VLOOKUP 函数的结果。

> 2.如果不确定查找值是否存在，但仍想抑制 #N/A 错误，可以在单元格中使用名为 IFERROR 的错误处理函数
```excel
=IFERROR(VLOOKUP(F43,F37:G41,2,FALSE),"")。
```
IFERROR 表示，如果 VLOOKUP 返回有效结果，则显示该结果，否则不显示任何内容 ("")。此处我们没有显示任何内容 ("")，但还可以使用数字（0、1、2 等）或文本，如“公式不正确”。 