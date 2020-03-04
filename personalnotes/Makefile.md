# Makefile
## 1. 显示规则
目标：依赖
[tab]命令

第一个目标为终极目标
. PHONY： 伪目标，只执行命令，不产生目标文件

## 2. 变量
* = 替换
* += 追加
* :=常量
* 变量使用：$（变量名）
* 使用环境变量：$$(HOME)

## 3. 隐含规则
* %.c 任意的c文件
* *.c 所有的c文件
%.o:%.c
    gcc -c %.c -o %.o
    #用任意的c文件生成对应的o文件

objs=main. o test. o
$(objs):%.o:%.c
    $(CC) -c $(CFLAGS) $< -o $@
对目标文件里的每个. o文件，用对应的. c文件编译，等价于：
main. o:main. c
    $(CC) -c $(CFLAGS) main. c -o main. o
test. o:test. c
    $(CC) -c $(CFLAGS) test. o -o test. c
    
## 4通配符
* $^ 所有的依赖文件
* $@ 所有的目标文件
* $< 所有依赖文件中的第一个文件
* $> 所有依赖文件中的最后一个文件


