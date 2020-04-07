# 30分钟复习shell

## 变量

```sh
# 变量名和等号之间不能有空格，这可能和你熟悉的所有编程语言都不一样。
value1=10

# 只读变量,用readonly 修饰
readonly value1
readonly value4=4

# 删除变量
unset testint2

#使用变量
echo ${value4}
echo $value4
```


## string

```sh
your_name="runoob"
# 拼接
greeting="hello, "$your_name" !"
greeting_1="hello, ${your_name} !"

#获取string len
echo 'greeting len:'${#greeting}

string="runiob is a great site"
#裁切
echo ${string:1:4} # unio

```


## 数组

```sh

# bash支持一维数组（不支持多维数组），并且没有限定数组的大小。
# 用括号来表示数组，数组元素用"空格"符号分割开。
array_name=(value0 value1 value2 value3)
# 获取全部元素
echo ${array_name[@]}
# 取得数组元素的个数
length=${#array_name[@]}
# 或者
length=${#array_name[*]}
# 取得数组单个元素的长度
lengthn=${#array_name[n]}

```


## 基本运算

| 运算符 | 说明   | 举例                       |
| ------ | ------ | -------------------------- |
| +      | 加法   | `expr $a + $b` 结果为 30   |
| -      | 减法   | `expr $a - $b` 结果为 -10  |
| *      | 乘法   | `expr $a \* $b` 结果为 200 |
| /      | 除法   | `expr $b / $a` 结果为 2    |
| %      | 取余   | `expr $b % $a` 结果为 0    |
| =      | 赋值   | a=$b 将把变量 b 的值赋给a  |
| ==     | 相等   | [ $a == $b ] 返回 false    |
| !=     | 不相等 | [ $a != $b ] 返回 true     |

```sh
# 原生bash不支持简单的数学运算，但是可以通过其他命令来实现，例如 awk 和 expr，expr 最常用。
# 乘号(*)前边必须加反斜杠(\)才能实现乘法运算；
val=$(expr $a + $b)
echo "a + b : $val"

val=$(expr $a - $b)
echo "a - b : $val"

val=$(expr $a \* $b)
echo "a * b : $val"

val=$(expr $b / $a)
echo "b / a : $val"

val=$(expr $b % $a)
echo "b % a : $val"
```

| 运算符 | 说明                                        | 举例            |
| ------ | ------------------------------------------- | --------------- |
| -eq    | 检测两个数是否相等,相等返回true             | `[ $a -eq $b ]` |
| -ne    | 检测两个数是否不相等,不相等返回true         | `[ $a -ne $b ]` |
| -gt    | 检测左边的数是否大于右边的,是则返回true     | `[ $a -gt $b ]` |
| -lt    | 检测左边的数是否小于右边的,是则返回true     | `[ $a -lt $b ]` |
| -ge    | 检测左边的数是否大于等于右边的,是则返回true | `[ $a -ge $b ]` |
| -le    | 检测左边的数是否小于等于右边的,是则返回true | `[ $a -le $b ]` |

```sh

if [ $a -eq $b ]; then
    echo "$a -eq $b : a 等于 b"
else
    echo "$a -eq $b: a 不等于 b"
fi
if [ $a -ne $b ]; then
    echo "$a -ne $b: a 不等于 b"
else
    echo "$a -ne $b : a 等于 b"
fi
if [ $a -gt $b ]; then
    echo "$a -gt $b: a 大于 b"
else
    echo "$a -gt $b: a 不大于 b"
fi
if [ $a -lt $b ]; then
    echo "$a -lt $b: a 小于 b"
else
    echo "$a -lt $b: a 不小于 b"
fi
if [ $a -ge $b ]; then
    echo "$a -ge $b: a 大于或等于 b"
else
    echo "$a -ge $b: a 小于 b"
fi
if [ $a -le $b ]; then
    echo "$a -le $b: a 小于或等于 b"
else
    echo "$a -le $b: a 大于 b"
fi

if [ $a -lt 100 -a $b -gt 15 ]; then
    echo "$a 小于 100 且 $b 大于 15 : 返回 true"
else
    echo "$a 小于 100 且 $b 大于 15 : 返回 false"
fi
if [ $a -lt 100 -o $b -gt 100 ]; then
    echo "$a 小于 100 或 $b 大于 100 : 返回 true"
else
    echo "$a 小于 100 或 $b 大于 100 : 返回 false"
fi
if [ $a -lt 5 -o $b -gt 100 ]; then
    echo "$a 小于 5 或 $b 大于 100 : 返回 true"
else
    echo "$a 小于 5 或 $b 大于 100 : 返回 false"
fi

if [[ ($a -lt 100) && ($b -gt 100) ]]; then
    echo "返回 true"
else
    echo "返回 false"
fi

if [[ $a -lt 100 || $b -gt 100 ]]; then
    echo "返回 true"
else
    echo "返回 false"
fi
```