
## Shell脚本编程
 
字符串中默认转义字符无效
 
 
``
test=2
test=$((test++))``
运行结果：3
 
`test=$(($test++))`
错误
 
 
 
位置变量`$9`以后应该为`$[10]`
```
$0　　　　　　　脚本的名称
$# 参数个数
$1,$2,$3....　　　第一个参数，第二个参数，第三个参数
$*　　参数列表
$@　　参数列表
```
### shell
 
和php一样的单引号、双引号语法
 
需要注意的是定义变量时，=两边都没有空格的（最蛋疼的语法，随手在必要的地方打上空格已经成为习惯了）
 
常量readonly，不是final，也不是const
 
变量在赋值（等号赋值、read赋值）时不加$，其余情况要加上$
 
可有可无的分号，习惯上不加分号
 
if后面的空格、[后面的空格和]前面的空格全部不能少！！！
 
0为真，1为假
 
### case语句
 
switch呢？switch呢？switch呢？ :x
 
```bash
case 值 in
模式1)
    command1
    command2
    command3
    ;;
模式2）
    command1
    command2
    command3
    ;;
*)
    command1
    command2
    command3
    ;;
esac
```
 
 
### 循环语句
 
for语句：
```bash
for 变量 in 列表
do
    command1
    command2
    ...
    commandN
done
```
其中if和elif后面都要加then
for  loop in 1 2 3 4 5
 
while语句
```
while command
do
   Statement(s) to be executed if command is true
done
```

 
### 注释
 
注释符只能是#，没有多行注释（My God）
```
########################
 
# 这是一个
 
#          多行注释
 
########################
```
多行注释小技巧：把要注释的代码用一对花括号括起来，定义成一个函数，没有地方调用这个函数，这块代码就不会执行，达到了和注释一样的效果。
 
### expr
 
不能是浮点数、*不是乘
