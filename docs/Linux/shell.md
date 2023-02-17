<!-- shell -->

### select in指令-选择交互
`select in`是 `Shell` 独有的一种循环，非常适合终端（Terminal）这样的交互场景.
使用示例:
```shell
#!/bin/bash
 
echo "What is your favourite OS?"
select name in "Linux" "Windows" "Mac OS" "UNIX" "Android"
do
    echo $name
done
echo "You have selected $name"
```
运行结果：
```shell
What is your favourite OS?
1) Linux
2) Windows
3) Mac OS
4) UNIX
5) Android
#? 4↙
You have selected UNIX
#? 1↙
You have selected Linux
#? 9↙
You have selected
#? 2↙
You have selected Windows
#?^D
```
`^D`表示按下 `Ctrl+D` 组合键，它的作用是结束 `select in` 循环.
但是我们更常用的是在select里加break推出循环.
> 注意，select 是无限循环（死循环），输入空值，或者输入的值无效，都不会结束循环，只有遇到 break 语句，或者按下 Ctrl+D 组合键才能结束循环。

**`select in`通常和`case`一起使用,完整示例如下:**
```shell
#!/bin/bash

echo "What is your favourite OS?"
select name in "Linux" "Windows" "Mac OS" "UNIX" "Android"
do
    case $name in
        "Linux")
            echo "Linux是一个类UNIX操作系统，它开源免费，运行在各种服务器设备和嵌入式设备。"
            break
            ;;
        "Windows")
            echo "Windows是微软开发的个人电脑操作系统，它是闭源收费的。"
            break
            ;;
        "Mac OS")
            echo "Mac OS是苹果公司基于UNIX开发的一款图形界面操作系统，只能运行与苹果提供的硬件之上。"
            break
            ;;
        "UNIX")
            echo "UNIX是操作系统的开山鼻祖，现在已经逐渐退出历史舞台，只应用在特殊场合。"
            break
            ;;
        "Android")
            echo "Android是由Google开发的手机操作系统，目前已经占据了70%的市场份额。"
            break
            ;;
        *)
            echo "输入错误，请重新输入"
    esac
done
```

