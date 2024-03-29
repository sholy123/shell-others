##  grep 命令

linux中一个强大的文本搜索工具，可以使用正则表达式搜索文本，并且把匹配的行打印出来，grep可以用于shell脚本，搜索返回一个状态值来说明搜索的状态，如果搜索成功，则返回0，如果搜索不成功，则返回1，如果搜索的文件不存在，则返回2，我们利用这些返回值就可以进行一些自动化的文本处理工作。

1. 命令格式

   ```shell
   grep [option] pattren file 
   ```

2. 命令功能

   用于过滤或者搜索特定字符，可以使用正则表达式配个多个命令使用，使用上十分灵活

3. 命令参数

   - -a 不要忽略二进制的数据
   - -A 显示行数，除了显示匹配到的行以外，并显示该行之后的内容。
   - -b 在显示符合样式的那一行之前，标出改行第一个字符的编号
   - -B 显示行数，显示匹配之前的行数
   - -c 计算符合样式的列数
   - -C 显示行数，显示所有的行数
   - -d 当指定查找为目录而不是文件的时候，必须使用该参数
   - -e 范本样式，指定字符串为查找文件内容的样式
   - -E 将样式延伸为普通表示法来使用
   - -f 规则文件，指定规则文件内容中含有一个或者多个规则样式
   - -F 将样式固定字符串的列表
   - -G 将样式视为普通的表示法来做
   - -h 在显示符合样式的那一行之前，不标示改行所属的文件名称
   - -i 忽略大小写的差别
   - -l 列出文件内容符合指定样式的文件名称
   - -s 不显示错误信息
   - -v 显示不包含匹配文本的所有行
   - -w 只显示全字符匹配文本的所有行
   - -x 只显示全列符合的列

4. 使用实例

   规则表达式符合正则表达式，使用正则表达式匹配即可

   1. 查找指定进程

      ```shell
      ps -ef | grep batch
      ```

   2. 查找指定的进程数

      ```shell
      ps -ef 、 grep -c sys
      ```

   3. 从文件中读取关键词进行搜索

      ```shell
      cat 1.txt | grep -f 2.txt
      ```

      指定2.txt为规则文件，将1.txt文件中内容按照2.txt文件中的规则进行匹配，输出所有的匹配行

   4. 从文件中查找关键字

      ```shell
      grep “linux” 1.txt
      ```

      从文件中找到相应的linux的字样

   5. 从多个文件中查找关键词

      ```shell
      grep -n file.txt file2.txt
      ```

      多个文件查找时，输出查找到的内容行时，会把文件的名字匹配在前面。