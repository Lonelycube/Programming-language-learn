# Perl 语言实验报告

[TOC]

## 实验 一、九九乘法表

### 一、代码

**1.代码一：**

```perl
#!/usr/bin/perl 

use strict;     # 严格模式，检查不合理语法错误
use warnings;   # 使用警告 
use utf8;   #使用utf8 编译告诉perl解析器 允许UTF-8在程序文本在当前的词法范围

for ( my $i = 1 ; $i <= 9 ; $i++ ) {
    for ( my $j = 1 ; $j <= $i ; $j++ ) {
        print "$j x $i = " . $i * $j;
        if   ( $j == $i ) { print "\n"; }
        else              { print "\t"; }
    }
}
```
**2.代码二：**

```perl
#!/usr/bin/perl 

use strict;     # 严格模式，检查不合理语法错误
use warnings;   # 使用警告
use utf8;  #使用utf8 编译告诉perl解析器 允许UTF-8在程序文本在当前的词法范围

for ( my $i = 1 ; $i <= 9 ; $i++ ) {
    for ( my $j = 1 ; $j <= $i ; $j++ ) {
        print "$j" . "x" . "$i" . "=" . $i * $j;
        if   ( $j == $i ) { print "\n"; }
        else              { print "\t"; }
    }
}
```

**3.输出结果：**

```perl
1*1=1
1*2=2   2*2=4
1*3=3   2*3=6   3*3=9
1*4=4   2*4=8   3*4=12  4*4=16
1*5=5   2*5=10  3*5=15  4*5=20  5*5=25
1*6=6   2*6=12  3*6=18  4*6=24  5*6=30  6*6=36
1*7=7   2*7=14  3*7=21  4*7=28  5*7=35  6*7=42  7*7=49
1*8=8   2*8=16  3*8=24  4*8=32  5*8=40  6*8=48  7*8=56  8*8=64
1*9=9   2*9=18  3*9=27  4*9=36  5*9=45  6*9=54  7*9=63  8*9=72  9*9=81
```

**4.格式化代码：**


```shell
#安装perltidy
sudo apt install perltidy
#sudo apt-get install perltidy

#保留原始文件， 格式化后的文件为*.tdy
perltidy script.pl

#备份原始文件为*.bak， 格式化后的文件使用原文件名
perltidy -b script.pl

#perltidy使用帮助
man perltidy
perltidy -h
```



### 二、注意事项：

1. `use strict`  :是提供给Perl编译器的指令，告诉编译器，如果perl代码中有不好的编码风格，那么提示编译失败。

​	**使用规范：**

	1.每一行perl语句要以分号;结尾
	2.所有变量要加上my来控制变量的作用域范围

2. `for循环`:用于多次执行一个语句序列，简化管理循环变量的代码。

​	**语法格式：**

```perl
for ( init; condition; increment ){
   statement(s);
}
# init 会首先被执行，且只会执行一次。
# 接下来，会判断 condition，如果为 true，则执行循环主体
# 执行完 for 循环主体后，控制流会跳回上面的 increment 语句
# 条件再次被判断。如果为 true，则执行循环，在条件变为 false 时，for 循环终止。
```



 ### 三、拓展延伸：

**修改九九乘法表代码，使输出的形式与原来的形式对称（即倒三角）：**

**1.代码修改如下：**

```perl
#!/usr/bin/perl 

use strict;     # 严格模式，检查不合理语法错误
use warnings;   # 使用警告
use utf8;  #使用utf8 编译告诉perl解析器 允许UTF-8在程序文本在当前的词法范围

for ( my $i = 9 ; $i >= 1 ; $i-- ) {
    for ( my $j = 1 ; $j <= $i ; $j++ ) {
        print "$j*$i=" . $i * $j;
        if   ( $j == $i ) { print "\n"; }
        else              { print "\t"; }
    }
}

```

**2.输出结果：**

```perl
1*9=9   2*9=18  3*9=27  4*9=36  5*9=45  6*9=54  7*9=63  8*9=72  9*9=81
1*8=8   2*8=16  3*8=24  4*8=32  5*8=40  6*8=48  7*8=56  8*8=64
1*7=7   2*7=14  3*7=21  4*7=28  5*7=35  6*7=42  7*7=49
1*6=6   2*6=12  3*6=18  4*6=24  5*6=30  6*6=36
1*5=5   2*5=10  3*5=15  4*5=20  5*5=25
1*4=4   2*4=8   3*4=12  4*4=16
1*3=3   2*3=6   3*3=9
1*2=2   2*2=4
1*1=1
```

----



## 实验二、序列和字符串

**1.存储DNA：**

```perl
#!/usr/bin/perl
use strict;
use warnings;
use utf8;

# 将字符串复制给标量$DNA
my $DNA = "ATCGATCGATCGATCGATCGATCGATCGATCG";

print "$DNA\n";

```

输出：

```
ATCGATCGATCGATCGATCGATCGATCGATCG
```

**2.拼接DNA片段：**

```perl
#!/usr/bin/perl
use strict;
use warnings;
use utf8;

#DNA的拼接 $DNA1 $DNA2
my $DNA1 = "AAAAAAAAAAAAAA";
my $DNA2 = "TTTTTTTTTTTTTT";
print '这是两条DNA片段:' . "\n\n"; # 利用符号 . 来将两个字符串拼接在一起
print "$DNA1\n";
print "$DNA2\n";

my $DNA3 = $DNA1 . $DNA2;   # 利用符号 . 来将两个字符串拼接在一起
print '这是拼接后的DNA:' . "\n\n";
print $DNA1,$DNA2,"\n";     # 利用符号 , 来将两个字符串拼接在一起
print "$DNA3\n\n";
```

输出：

```
这是两条DNA片段:

AAAAAAAAAAAAAA
TTTTTTTTTTTTTT

这是拼接后的DNA:

AAAAAAAAAAAAAATTTTTTTTTTTTTT
AAAAAAAAAAAAAATTTTTTTTTTTTTT

```

**3.DNA转录：**

```perl
#!/usr/bin/perl
use strict;
use warnings;
use utf8;
# DNA的转录
my $DNA1 = "AATTCCTT\n";
print "这是DNA编码链：\n\n";
print $DNA1,"\n\n";
my $RNA = $DNA1;
$RNA =~ s/T/U/g;                   # =~ 为绑定操作符，只对$RNA进行相关操作
print "这是转录出的RNA:\n\n";
print $RNA,"\n";
```

输出：

```
这是DNA编码链：

AATTCCTT


这是转录出的RNA:

AAUUCCUU

```

**涉及命令：**

> **$RNA =~ s/T/U/g;**  将$RNA中的T替换为U。
>
> **s:** 替换符号
>
> **g:**对全局进行操作

**4.反向互补：**

```perl
#!/usr/bin/perl
use strict;
use warnings;
use utf8;
# 反向互补
my $dna = 'AAAATTTAAATTTCCCGGG';
print "这是dna：\n\n";
print "$dna\n\n";

my $revcom = reverse $dna;    # reverse：取反。将DNA序列取反后赋值给$revcom
$revcom =~ s/A/T/g;           # 先将$revcom中的A替换为T；    
$revcom =~ s/T/A/g;           # 再将$revcom中的T替换为A；
$revcom =~ s/C/G/g;           # 再将$revcom中的C替换为G；
$revcom =~ s/G/C/g;           # 再将$revcom中的G替换为C；
print "这是互补dna：\n\n";   
print "$revcom\n\n";

print "发现出错了\n";
print "重做！\n";
my $revcom = reverse $dna;
$revcom =~ tr/ACGTacgt/TGCAtgca/; # 对序列中的碱基替换必须要同时替换。

print "下面是正确结果：\n";
print "$revcom\n";
exit;

```

输出：

```
这是dna：
AAAATTTAAATTTCCCGGG

这是互补dna：
CCCCCCAAAAAAAAAAAAA

发现出错了
重做！

下面是正确结果：
CCCGGGAAATTTAAATTTT

```

**涉及函数：**

> **$revcom =~ tr/ACGTacgt/TGCAtgca/;**  
>
> 将$revcom中的ACGTacgt翻译为 TGCAtgca ，每个字符一一对应；
>
> **tr：**翻译命令



**5.从文件中读取数据：**

```perl
#!/usr/bin/perl
use strict;
use warnings;
use utf8;

open(FD,"a.txt") or die("Can not open the file!$!n");
# FD为文件句柄，保存文件名a.txt 
# 打开文件a.txt,打不开则输出错误信息。

my $dna = <FD>; 
# 将文件中的第一行数据赋值给变量$dna

close FD;      # 关闭文件
print $dna;
```

输出:

```perl
# a.txt文件中内容为：gggggggggggggggggggg

gggggggggggggggggggg
```

**总结：**

本次实验涉及对字符串变量的一些操作，如赋值、拼接、替换、提取文件信息等。

1.拼接DNA有多种方法:

```perl
$dna3=$dna1 . $dna2;
$dna3=$dna1$dna2;
print $dna1,$dna2;
...
```

2.DNA转录（多个碱基替换）：

需同时进行替换，不能先替换一种碱基，在替换另一种，如DNA序列为 AAATTT，如果先替换A=>T ，再替换T=>A,那么结果为AAAAAA，并不是TTTAAA。

3.提取文件信息：

打开文件，提取完信息后必须关闭文件。





---

## 实验三、基序和循环

[TOC]

### 一、流程控制

**流程控制(flow control )：**是电脑运算领域的用语，意指在程序运行时，个别的指令（或是陈述、子程序）运行或求值的顺序。 

**默认：**除非明确指明不按顺序执行，否则程序将从最顶端的第一个语句开始，顺序执行到最底端的最后一个语句。 

**分类：**

1. 条件判断：只在条件测试成功的前提下执行相应的语句，否则直接跳过这些语句
2. 循环：一直重复语句，直到相应的测试失败为止

------

#### 1.条件判断

##### if

**格式：**

```perl
if(条件测试){
   执行
}
```

**工作原理 :**

1. 条件测试的结果为真（true）或者为假（false）
2. 如果测试结果为真，后面的语句就会被执行
3. 如果测试结果为假，后面的语句就不会执行，直接被跳过 

**1.if ：真**

```perl
# =表示赋值， ==表示数字相等

if( 1 == 1 ) {
print "1 equals 1\n\n";
}
# 1==1为真，如果为真，就输出：1 equals 1

if( 1 ) {
print "1 evaluates to true\n\n"；
}
# 1为真，如果为真，就输出：1 evaluates to true
```

**2.if：假**

```perl
if( 1 == 0 ) {
print "1 equals 0\n\n";
}
# 测试结果为假，因此不输出

if( 0 ) {
print "0 evaluates to true\n\n";
}
# 测试结果为假，因此不输出
```

**3.if：简写**

```perl
# 两种写法完全等价
# 比较“标准”， 易读易懂
if( 1 == 1 ) {
print "1 equals 1\n\n";
}

# 更加简洁
print "1 equals 1\n\n" if (1 == 1);
# 类比自然语言（英语）
# If you build it, they will come.
# They will come if you build it.
```

------

##### if-else

**格式：**

```perl
if(条件测试){
    执行
} else{
    执行
}
```

**1.if-else：真**

```perl
if( 1 == 1 ) {
print "1 equals 1\n\n";
} else {
print "1 does not equal 1\n\n";
}
# 如果1=1，那么输出1 equals 1；否则输出1 does not equal 1。
```

**2.if-else：假**

```perl
if( 1 == 0 ) {
print "1 equals 0\n\n";
} else {
print "1 does not equal 0\n\n";
}
# 如果1=0，那么输出1 equals 0；否则输出1 does not equal 0。
```

------

##### if-elsif-else 

**格式：**

```perl
if(条件测试){
    执行
} elsif(条件测试){
    执行
} else{
    执行
}
```

**例1：**

```perl
#!/usr/bin/perl -w

$word = 'MNIDDKL';

if($word eq 'QSTVSGE') {
print "QSTVSGE\n";
} elsif($word eq 'MRQQDMISHDEL') {
print "MRQQDMISHDEL\n";
} elsif ( $word eq 'MNIDDKL' ) {
print "MNIDDKL--the magic word!\n";
} else {
print "Is \"$word\" a peptide? This program is not sure.\n";
}
exit;
# 如果$word的字符串等于QSTVSGE，输出 QSTVSGE。
# 如果$word的字符串等于MRQQDMISHDEL，输出 MRQQDMISHDEL。
# 如果$word的字符串等于MNIDDKL，输出 MNIDDKL--the magic word!
# 否则输出 Is " $word " a peptide? This program is not sure.
```

------

##### unless

**工作原理：**

1. unless 和 if 完全相反
2. 如果测试结果为真，语句会直接被跳过而不执行
3. 如果测试结果为假，相应的语句会被执行 

**格式：**

```perl
unless(条件测试){
    执行
}
```

**unless | if**

```perl
unless ( 1 == 0 ) {
print "1 does not equal 0\n\n";
}

if ( 1 != 0 ) {
print "1 does not equal 0\n\n";
}

if ( !(1 == 0) ) {
print "1 does not equal 0\n\n";
}
# 最后都能输出：1 does not equal 0
```

**条件测试相关符号**

| 含义       | 符号                                    |
| :--------- | --------------------------------------- |
| 数字比较   | ==, !=, <, >, <=, >=                    |
| 字符串比较 | eq, ne, lt, gt, le, ge                  |
| 文件测试   | -e, -s, -z, -f, -d, -l, -r, -w, -x, ... |

**真假判定 ：**

1. 如果是数字：0（0, 0.0, -0.0, ……）为假，其他所有数字都为真
2. 如果是字符串：空字符串（用 "" 或 '' 表示）为假，其他所有字符串都为真
   注意：字符串 '0' 或 "0"（和数字 0 是同一个标量值）是唯一被当成假的非空字符串
3. 如果既不是数字也不是字符串，先转换成数字或字符串再行判断 





#### 2.循环

**工作原理：**只要测试为真，就会重复执行被成对大括号包裹起来的语句块。 

------

##### while | until

**格式：**

```perl
while(控制语句){
    执行
}
# 如果条件为真，则执行循环。

until(控制语句){
    执行
}
# 如果条件为假，则执行循环。
```

**例1：**

```perl
$count = 0;
until ( $count >= 10 ) {
print "count is now $count\n";
$count += 2;
}

$count = 0;
while ( $count < 10 ) {
print "count is now $count\n";
$count += 2;
}

$count = 0;
while ( !($count >= 10) ) {
print "count is now $count\n";
$count += 2;
}
# 三个都能输出以下内容：
count is now 0
count is now 2
count is now 4
count is now 6
count is now 8
```

**例2：**

```perl
#!/usr/bin/perl -w

# 预先已创建了一个dna_1.txt文件，里面有三行序列
$dnafilename = 'dna_1.txt';

# 利用 unless 进行打开文件并读取文件信息操作
# open：打开文件，是一个系统调用
unless ( open( DNA, $dnafilename ) ) {
print "Could not open file $dnafilename!\n";
exit;
}

# 利用 while 循环，将dna_1.txt文件中的每一行信息输出。 
# 先进行条件判断，执行$dna = <DNA>，如果能执行（为真），则执行循环体，之后返回再条件判断。
while ( $dna = <DNA> ) {
print " ###### Here is the next line of the file:\n";
print $dna;
}

# 关闭dna_1.txt文件。
close DNA;
exit;
```

　输出：

```shell
###### Here is the next line of the file:
CGATCGATCGTACGTAGCTAGCTAGCTAGCTAGCTAGCTAGCTAGC
###### Here is the next line of the file:
CGAGCATCGATCGTAGCTAGCATCGATCGTAGCTAGCTAGCTACTACGA
###### Here is the next line of the file:
TAGCTAGCTACTATCAGCGAGCTAGCTACGTAGCTAGCTACGATCGT
```

------

##### for | foreach

在 Perl 解析器里， foreach 和 for 这两个关键字实际上等价的。当Perl 看到其中之一时，就好像看到了另一个。 

```perl
for ( 1..10 ) {
print "I can count to $_!\n";
}

foreach ( 1..10 ) {
print "I can count to $_!\n";
}

for ( $i=1; $i<=10; $i++ ) {
print "I can count to $i!\n";
}
# 三个输出的结果相同
```

　输出:

```perl
I can count to 1!
I can count to 2!
I can count to 3!
I can count to 4!
I can count to 5!
I can count to 6!
I can count to 7!
I can count to 8!
I can count to 9!
I can count to 10!
```

------





### 二、查找基序

**基序(motif) ：**特定的 DNA 片段（如 DNA 调控元件）或蛋白质片段（如保守区域）。

> 用正则表达式表征基序；
>
> 在字符串中进行查找 。

**例1：**

```perl
#!/usr/bin/perl -w
# 程序5.3
# 询问用户想要查找基序的蛋白质序列文件。
print "Please type the filename of the protein sequence data: ";
$proteinfilename = <STDIN>;

# 利用chomp命令，将输入文件时的回车符删去。
chomp $proteinfilename;

# 利用unless、open命令，打开蛋白质序列文件。
unless ( open( PROTEINFILE, $proteinfilename ) ) {
print "Cannot open file \"$proteinfilename\"\n\n";
exit;
}

# 读取文件中的序列信息，并将每行序列信息存到数组 @protein 中去；最后关闭文件。
@protein = <PROTEINFILE>;
close PROTEINFILE;

#将数组中的元素用 join 命令组合成一个字符串；并将其中的空白字符删去。
$protein = join( '', @protein );
$protein =~ s/\s//g;

#利用 do-until循环进行基序的查找；
do {
print "Enter a motif to search for:";
$motif = <STDIN>;

# 用chomp函数删除变量最后的空白字符。
chomp $motif;

if ( $protein =~ /$motif/ ) {         # 如果$protein中能匹配到$motif,就输出"I found it!"
print "I found it!\n\n";
}
else {
print "I couldn\'t find it.\n\n";     # 否则输出I couldn't find it.
}
# exit on an empty user input
} until ( $motif =~ /^\s*$/ );        # 直到用户输入为空或空白时停止基序的查找。
# exit the program
exit;
```

------



### 三、计数核苷酸

**例1：**

```perl
#!/usr/bin/perl
# 程序5.4
use warnings;

print "Please type the filename of the DNA sequence data: ";
$dna_filename = <STDIN>;          # 获取DNA序列文件名
chomp $dna_filename;              # 删除末尾空字符
unless ( open( DNAFILE, $dna_filename ) ) {
    print "Cannot open file \"$dna_filename\"\n\n";
    exit;                           
}
@DNA = <DNAFILE>;                 # 将文件中的每一行都存到数组@DNA中去
close DNAFILE;                    # 关闭DNA序列文件
$DNA = join('',@DNA);             # 将数组@DNA的每个元素用空分隔，拼接为一个字符串变量。
$DNA =~ s/\s//g;                  # 删除字符串中的空白字符
@DNA = split('',$DNA);            # 将每个字符用空分隔为一个元素，保存到数组@DNA中去。
$count_of_A = 0;                  # 初始化碱基数为0
$count_of_C = 0;
$count_of_G = 0;
$count_of_T = 0;
$errors = 0;

foreach $base (@DNA) {            # 利用foreach循环，对数组中的碱基元素进行计数
if ( $base eq 'A' ) {
++$count_of_A;
}
elsif ( $base eq 'C' ) {
++$count_of_C;
}
elsif ( $base eq 'G' ) {
++$count_of_G;
}
elsif ( $base eq 'T' ) {
++$count_of_T;
}
else {
print "!!!!!!!! Error - I don\'t recognize thisbase: $base\n";
++$errors;
}
}
print "A = $count_of_A\n";
print "C = $count_of_C\n";
print "G = $count_of_G\n";
print "T = $count_of_T\n";
print "errors = $errors\n";

exit;

```

输出：

```
[kongyongqiang@BX ~/perl5/test1]$ perl jishu_5.4.pl
Please type the filename of the DNA sequence data: NM_021964.txt
A = 3033
C = 1608
G = 1801
T = 3132
errors = 0
```



**例2：**

```perl
#!/usr/bin/perl -w
# 程序5.6：计数核苷酸
print "please type the filename of DNA sequence data:";

$dna_file = <STDIN>;
chomp $dna_file;

open(FD,$dna_file) or die "Error!\n";
@DNA = <FD>;

# 如果文件类型为fasta，则删掉第一行；
if ($dna_file =~ /\.fasta$/){
shift @DNA;
}
close FD;

$DNA = join('',@DNA);
$DNA =~ s/\s//g;

$count_of_A = 0;
$count_of_C = 0;
$count_of_G = 0;
$count_of_T = 0;
$errors = 0;

# 不用将DNA序列转换维数组，而是直接对字符串进行substr截取操作来进行计数。
for ( $position = 0 ; $position < length $DNA ; ++$position ) {
        $base = substr( $DNA, $position, 1 );         
        # 从序列开头开始，每次将一个碱基赋值到$base中去。
        # 之后用if判断来进行计数。
        if ( $base eq 'A' ) {
                ++$count_of_A;
        }
        elsif ( $base eq 'C' ) {
                ++$count_of_C;
        }
        elsif ( $base eq 'G' ) {
                ++$count_of_G;
        }
        elsif ( $base eq 'T' ) {
                ++$count_of_T;
        }
        else {
                print "!!!!!!!! Error - I don\'t recognize this base:
                $base\n";
                ++$errors;
        }
}
print "A = $count_of_A\n";
print "C = $count_of_C\n";
print "G = $count_of_G\n";
print "T = $count_of_T\n";
print "errors = $errors\n";

exit;
```

输出：

```
[kongyongqiang@BX ~/perl5/test1]$ perl jishu_5.6.pl
please type the filename of DNA sequence data:NM_021964.fasta
A = 3032
C = 1608
G = 1801
T = 3132
errors = 0
```



**例3：**

```perl
#!/usr/bin/perl

print "Please type the filename of the DNA sequence data: ";
$dna_filename = <STDIN>;
chomp $dna_filename;

unless ( -e $dna_filename ) {
print "File \"$dna_filename\" doesn\'t seem to exist!!\n";
exit;
}

unless ( open( DNAFILE, $dna_filename ) ) {
print "Cannot open file \"$dna_filename\"\n\n";
exit;
}
@DNA = <DNAFILE>;
close DNAFILE;
$DNA = join( '', @DNA );
$DNA =~ s/\s//g;
$a = 0;
$c = 0;
$g = 0;
$t = 0;
$e = 0;

while ( $DNA =~ /a/ig ) { $a++ }  # 利用模式匹配，从头开始，匹配一次，计数值+1
while ( $DNA =~ /c/ig ) { $c++ }
while ( $DNA =~ /g/ig ) { $g++ }
while ( $DNA =~ /t/ig ) { $t++ }
while ( $DNA =~ /[^acgt]/ig ) { $e++ }

print "A=$a C=$c G=$g T=$t errors=$e\n";
$outputfile = "countbase";        # 将最终得到的碱基数目写入到文件countbase中去。
unless ( open( COUNTBASE, ">$outputfile" ) ) {
print "Cannot open file \"$outputfile\" to write to!!\n\n";
exit;
}
print COUNTBASE "A=$a C=$c G=$g T=$t errors=$e\n";
close(COUNTBASE);
exit;

```

输出：

```
[kongyongqiang@BX ~/perl5/test1]$ perl jishu_5.7.pl
Please type the filename of the DNA sequence data: NM_021964.fasta
A=3037 C=1610 G=1802 T=3136 errors=63
```

### 四、总结

此次试验对DNA序列进行基序查找，以及计算DNA序列中的每种核苷酸的数目。

**1.条件判断与循环**

在编写时，应该仔细考虑好条件与执行的对应关系，为真的执行，还是为假的时候执行。

**2.查找基序**

在获取输入时，应该用chomp函数将变量后的空字符删去。

**3.计数核苷酸**

三种计数方法：

```
1. 利用foreach循环和if判断对数组@DNA进行计数
2. 利用for循环、substr函数和if判断对字符串$DNA进行计数
3. 利用模式匹配方法对$DNA进行计数，每匹配一次，数值加1，最后得到总的每种核苷酸数目。
```



---

## 实验四、子程序

[TOC]

### 一、子程序

**例1：**

```perl
#!/usr/bin/perl -w

$dna = 'CGACGTCTTCTCAGGCGA';
$longer_dna = addACGT($dna);
print "I added ACGT to $dna and got $longer_dna\n\n";
exit;
# 子程序addACGT：在字符串末尾加上ACGT字符串。
sub addACGT {
my ($dna) = @_;  # 将参数传递给子程序。
$dna .= 'ACGT';
return $dna;     # 返回参数值。
}

```

输出：

```
I added ACGT to CGACGTCTTCTCAGGCGA and got CGACGTCTTCTCAGGCGAACGT

```



**例2：**

```perl
#!/usr/bin/perl

$dna = 'AAAAA';
$result = A_to_T($dna);
print "I changed all the A's in $dna to T's and got $result\n\n";
exit;

###############
# 子程序：A_to_T： 将dna序列中的A替换为T
sub A_to_T {
my ($input) = @_;
my $dna = $input;
$dna =~ s/A/T/g;
return $dna;
}
```

输出：

```
I changed all the A's in AAAAA to T's and got TTTTT

```



**例3：**

```perl
#!/usr/bin/perl

use strict;
my ($USAGE) = "$0 DNA\n\n";  #如果命令行无输入，就输出“程序名 DNA”
unless (@ARGV) {
print $USAGE; exit;
}
my ($dna) = $ARGV[0];   # 获取命令行输入
my ($num_of_Gs) = countG($dna);
print "\nThe DNA $dna has $num_of_Gs G\'s in it!\n\n";
exit;


#################################
# 子程序countG :计算dna序列中的G含量
sub countG {
my ($dna) = @_;
my ($count) = 0;
$count = ( $dna =~ tr/Gg// );  # 将DNA中的G/g 进行tr翻译，每进行一次，计数+1
return $count;           # 返回参数值$count
}

```

输出：

```
[kongyongqiang@BX ~/perl5/test1]$ perl countG_6.3.pl ATCGGGGGCATGCTAGC

The DNA ATCGGGGGCATGCTAGC has 7 G's in it!

```

### 二、 子程序bug

**例1：**

```perl
#!/usr/bin/perl
# 输入两个碱基，对dna进行匹配，如果存在，就将从匹配位置到结束位置的碱基序列都输出。如没有输入，则默认查找TA。
my $dna = 'CGACGTCTTCTAAGGCGA';
my @dna;
my $receivingcommittment;
my $previousbase = '';
my $subsequence = '';
if (@ARGV) {                     # 获取命令行输入
my $subsequence = $ARGV[0];
}
else {
$subsequence = 'TA';             # 命令行无输入，则默认为TA
}

my $base1 = substr( $subsequence, 0, 1 );
my $base2 = substr( $subsequence, 1, 1 );
@dna = split( '', $dna );
foreach (@dna) {                 # 对数组@DNA进行递归循环
if ($receivingcommittment) {     # 如过$receivingcommittment为1，则一直输出。
print;
next;
}
elsif ( $previousbase eq $base1 ){  # 如果匹配到第一个字符，在判断第二个字符是否匹配 
if (/$base2/) {
print $base1, $base2; 
$recievingcommitment = 1;         # 将1赋值给 $recievingcommitment
}
}
$previousbase = $_;               # 将默认输出赋值给$previousbase
}
print "\n";
exit;
```

输出：

```shell
$ perl perl_6.4.pl AA

# 并没有得到想要的结果
```



**修改bug后的代码：**

```perl
#!/usr/bin/perl

my $dna = 'CGACGTCTTCTAAGGCGA';
my @dna;
my $receivingcommittment;
my $previousbase = '';
my $subsequence = '';
if (@ARGV) {
 $subsequence = $ARGV[0];     # 删去了 my
}
else {
$subsequence = 'TA';
}

my $base1 = substr( $subsequence, 0, 1 );
my $base2 = substr( $subsequence, 1, 1 );
@dna = split( '', $dna );
foreach (@dna){
if ( $receivingcommittment) {
print;
next;
}elsif ( $previousbase eq $base1 ) {
if ( /$base2/) {
print $base1, $base2;
$receivingcommittment = 1;    # 上个程序的变量名写错了，更改之后为$receivingcommittment
}
}


$previousbase = $_;
}
print "\n";
exit;

```

**结果：**

```shell
$ perl perl_6.4.pl AA
AAGGCGA
$ perl perl_6.4.pl TA
TAAGGCGA
# 修改成功，得到理想的结果输出
```





**例2：**

```perl
#!/usr/bin/perl

use warnings; use strict;
my $dna = "CGACGTCTTCTAAGGCGA";
my $subsequence = @ARGV ? $ARGV[0] : "TC"; 
# 如果@ARGV存在，那么将$ARGV[0]赋值给$subsequence,否则将TC赋值给$subsequence。

my @dna = split "", $dna;
my $base1 = substr( $subsequence, 0, 1 );
my $base2 = substr( $subsequence, 1, 1 );
for ( my $i = 0 ; $i < @dna - 1 ; $i++ ) {
if ( $dna[$i] eq $base1 ) {
if ( $dna[ $i + 1 ] eq $base2 ) {
print join "", @dna[ $i .. $#dna ];
print "\n";
# last;
    }
  }
}

```

输出：

```
TCTTCTAAGGCGA
TCTAAGGCGA

```

### 三、总结

此次试验进行了子程序的编写和bug的调试。

**1.子程序**

参数传递要搞清楚，是否要把子程序的值返回给主程序。

**2.bug**

编写子程序时，要考虑清楚对那些变量进行声明，那些变量应为全局变量，哪些应为局部变量。

注意变量名不要写错。



## 实验五、突变和随机化

[TOC]

### 一、随机化程序

**例1：随机生成小故事**

```perl
#!/usr/bin/perl

use strict;
use warnings;
my $count;              # 初始化变量
my $input;
my $sentence;
my $story;

my @nouns = (           # 构建数组@nouns（名词）
'Dad', 'TV', 'Mom', 'Groucho','Rebecca', 'Harpo', 'Robin Hood', 'Joe and Moe',
);
my @verbs = (           # 构建数组@verbs（动作）
'ran to', 'giggled with', 'put hot sauce into the orange juice of','exploded', 'dissolved', 'sang stupid songs with','jumped with',
); 
my @prepositions = (    # 构建数组@prepositions（地点）
'at the store',
'over the rainbow',
'just for the fun of it',
'at the beach',
'before dinner',
'in New York City',
'in a dream',
'around the world',
);

srand( time | $$ );     # 为随机数生成器设置种子
do {
$story = '';            # for循环随机生成6个句子构成一个故事
for ( $count = 0 ; $count < 6 ; $count++) {
$sentence =
$nouns[ int( rand( scalar @nouns ) ) ] . " ". $verbs[ int( rand( scalar @verbs ) ) ] . " ". $nouns[ int( rand( scalar @nouns ) ) ] . " ". $prepositions[ int( rand( scalar @prepositions ) ) ] . '. ';
$story .= $sentence;
}
print "\n", $story, "\n";
print "\nType \"quit\" to quit, or press Enter to continue: ";
$input = <STDIN>;      # 获取输入，判断是否继续
} until ( $input =~ /^\s*q/i );
exit;
```

输出：

```
Joe and Moe ran to Joe and Moe around the world. Dad sang stupid songs with Rebecca at the beach. Joe and Moe exploded Harpo over the rainbow. TV sang stupid songs with Groucho in New York City. Groucho dissolved Dad just for the fun of it. Dad sang stupid songs with TV over the rainbow.

Type "quit" to quit, or press Enter to continue:

Robin Hood dissolved TV at the store. Groucho put hot sauce into the orange juice of Robin Hood over the rainbow. Rebecca dissolved Joe and Moe at the beach. Rebecca exploded Dad just for the fun of it. Groucho ran to TV just for the fun of it. Joe and Moe sang stupid songs with TV before dinner.

Type "quit" to quit, or press Enter to continue:

TV dissolved Dad just for the fun of it. Dad exploded Dad in a dream. Mom giggled with Dad around the world. Dad giggled with TV at the store. Groucho giggled with Harpo at the store. Robin Hood put hot sauce into the orange juice of Harpo at the store.
...
```

### 二、模拟DNA突变

**例1：产生随机位置**

```perl
#!/usr/bin/perl

use warnings;
use strict;
my $dna = 'AACCGTTAATGGGCATCGATGCTATGCGAGCT';
srand( time | $$ );    # 设置随机数种子
for ( my $i = 0 ; $i < 20 ; ++$i ) {
    print randomposition($dna), " ";
}
print "\n";
exit;

##########################################
# 产生随机位置
sub randomposition {
    my ($string) = @_;
    return int( rand( length($string) ) );
}
```

结果：

```shell
18 3 26 12 3 18 27 17 6 31 5 23 3 0 28 3 31 16 18 16
```

**例2：产生随机碱基**

```perl
#!/usr/bin/perl

my @nucleotides = ( 'A', 'C', 'G', 'T' );
srand( time | $$ );
for ( my $i = 0 ; $i < 20 ; ++$i ) {
    print randomnucleotide(@nucleotides), " ";
}
print "\n";
exit;

############################################
# 产生随机碱基
sub randomnucleotide {
    my (@nucs) = @_;
    return $nucs[ rand @nucs ];
}
```

结果：

```shell
C G G G C G A C C G G T G C C C G C T G

```



**例3：模拟DNA突变**

```perl
#!/usr/bin/perl

use strict;
use warnings;

my $DNA = 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA';
my $i;
my $mutant;
srand( time | $$ );
$mutant = mutate($DNA);
print "\nMutate DNA\n\n";
print "\nHere is the original DNA:\n\n";
print "$DNA\n";
print "\nHere is the mutant DNA:\n\n";
print "$mutant\n";
print "\nHere are 10 more successive mutations:\n\n";

for ( $i = 0 ; $i < 10 ; ++$i ) {
    $mutant = mutate($mutant);
    print "$mutant\n";
}

######################################################
# 突变过程
sub mutate {
    my ($dna)      = @_;
    my ($position) = randomposition($dna);    # 获取随机突变位置
    my ($newbase)  = randomnucleotide();      # 获取要突变成为的碱基
    substr( $dna, $position, 1, $newbase )
      ;             # 将该位置的碱基替换为突变后的碱基
    return $dna;    # 将突变后的DNA序列传递回去
}

######################################################
# 随机碱基
sub randomnucleotide {
    my (@nucleotides) = ( 'A', 'C', 'G', 'T' );
    return randomelement(@nucleotides);
}

######################################################
# 随机位置
sub randomposition {
    my ($string) = @_;
    return int rand length $string;
}

######################################################
# 随机产生数组中的一个元素
sub randomelement {
    my (@array) = @_;
    return $array[ rand @array ];
}

```

结果：

```shell
Mutate DNA


Here is the original DNA:

AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

Here is the mutant DNA:

AAAAATAAAAAAAAAAAAAAAAAAAAAAAA

Here are 10 more successive mutations:

AAAAATAAAAAAAAAAAAAAATAAAAAAAA
AAAAATAAAAAAAAAAAAAAACAAAAAAAA
AAAAATAAAAAAAAAAAAAAACAAGAAAAA
AAAAATAAAAAAAAATAAAAACAAGAAAAA
AAAAATAAAAAAAAATAAAAACAAGATAAA
AAAAATAAAAAAAAATAAAAAGAAGATAAA
AAATATAAAAAAAAATAAAAAGAAGATAAA
AAATATAAAAAAAAATAAAAAGAAGATAAT
AAATATAAAAACAAATAAAAAGAAGATAAT
AAATATAAAAACAAATAAAAAGAAGATAAT
```



### 三、生成随机DNA

**例1：生成随机DNA**

```perl
#!/usr/bin/perl

use strict;
use warnings;

my $size_of_set    = 12;
my $maximum_length = 5;
my $minimum_length = 10;
my @random_DNA     = ();
srand( time | $$ );

@random_DNA =
  make_random_DNA_set( $minimum_length, $maximum_length, $size_of_set );
print "Here is an array of $size_of_set randomly generated DNA sequences\n";
print "with lengths between $minimum_length and $maximum_length:\n\n";

foreach my $dna (@random_DNA) {    # 循环输出随机DNA序列
    print "$dna\n";
}
print "\n";
exit;

##############################################
# 产生随机DNA序列
sub make_random_DNA_set {
    my ( $minimum_length, $maximum_length, $size_of_set ) = @_;
    my $length;      # 初始化
    my $dna;
    my @set;

    for ( my $i = 0 ; $i < $size_of_set ; ++$i ) {
        $length = randomlength( $minimum_length, $maximum_length );
        $dna = make_random_DNA($length);
        push( @set, $dna );
    }
    return @set;
}

#############################################
# 产生随机长度
sub randomlength {
    my ( $minlength, $maxlength ) = @_;
    return ( int( rand( $maxlength - $minlength + 1 ) ) + $minlength );
}

#############################################
#  产生随机DNA
sub make_random_DNA {
    my ($length) = @_;
    my $dna;
    for ( my $i = 0 ; $i < $length ; ++$i ) {
        $dna .= randomnucleotide();
    }
    return $dna;
}

#############################################
#产生随机碱基
sub randomnucleotide {
    my (@nucleotides) = ( 'A', 'C', 'G', 'T' );
    return randomelement(@nucleotides);
}

############################################
# 产生随机元素
sub randomelement {
    my (@array) = @_;
    return $array[ rand @array ];
}

```

结果：

```shell
Here is an array of 12 randomly generated DNA sequences
with lengths between 10 and 5:

ACCACACT
TAACAGCA
CGAGGGAC
GGAAACGCTA
AGTTCGCA
ACGTAGTATA
CAAAACGA
CTCGCCTAA
GATGGTCT
TCGAGCTT
GCCGGACTTG
CCGATAGAG

```

### 四、分析DNA

**例1：分析DNA**

```perl
#!/usr/bin/perl

use warnings;
use strict;

my $percent;
my @percentages;
my $result;
my @random_DNA = ();
srand( time | $$ );
@random_DNA = make_random_DNA_set( 10, 10, 10 );
for ( my $k = 0 ; $k < scalar @random_DNA - 1 ; ++$k ) {
    for ( my $i = ( $k + 1 ) ; $i < scalar @random_DNA ; ++$i ) {
        $percent = matching_percentage( $random_DNA[$k], $random_DNA[$i] );
        push( @percentages, $percent );
    }
}

$result = 0;

foreach $percent (@percentages) {
    $result += $percent;
}
$result = $result / scalar(@percentages);
$result = int( $result * 100 );
print "In this run of the experiment, the average percentage of \n";
print "matching positions is $result%\n\n";

exit;

###############################################
# 计算比对的一致率
sub matching_percentage {
    my ( $string1, $string2 ) = @_;
    my ($length) = length($string1);
    my ($position);
    my ($count) = 0;

    for ( $position = 0 ; $position < $length ; ++$position ) {
        if (
            substr( $string1, $position, 1 ) eq
            substr( $string2, $position, 1 ) )
        {
            ++$count;
        }
    }
    return $count / $length;
}

##############################################
# 产生随机DNA
sub make_random_DNA_set {
    my ( $minimum_length, $maximum_length, $size_of_set ) = @_;
    my $length;
    my $dna;
    my @set;
    for ( my $i = 0 ; $i < $size_of_set ; ++$i ) {
        $length = randomlength( $minimum_length, $maximum_length );
        $dna = make_random_DNA($length);
        push( @set, $dna );
    }
    return @set;
}
#############################################
# 产生随机长度
sub randomlength {
    my ( $minlength, $maxlength ) = @_;
    return ( int( rand( $maxlength - $minlength + 1 ) ) + $minlength );
}

#############################################
# 产生一条随机Dna
sub make_random_DNA {
    my ($length) = @_;
    my $dna;
    for ( my $i = 0 ; $i < $length ; ++$i ) {
        $dna .= randomnucleotide();
    }
    return $dna;
}

############################################
# 产生随机碱基
sub randomnucleotide {
    my (@nucleotides) = ( 'A', 'C', 'G', 'T' );
    return randomelement(@nucleotides);
}

#############################################
# 产生随机元素
sub randomelement {
    my (@array) = @_;
    return $array[ rand @array ];
}

```



结果：

```shell
$ perl random_7.4.pl.tdy
GTTGGAACAG
TCAGTAAAAT
TCGAGCCCTC
ATGTGTGTAG
CAAAGTCGCC
CTATATGCAT
ACTGTACGCG
TTACATTGCA
GATGCGGGTG
CGCCGGACCA
In this run of the experiment, the average percentage of
matching positions is 22%

$ perl random_7.4.pl.tdy
GCCAAGAGAC
ACTTAGAGAG
TACATTAGCG
ACGATTACGT
CAGTTTGGAT
CAAATTGTCA
TCTGCCGACT
CTCAACCCAT
TTGCTTATGC
CTCCGCTCAT
In this run of the experiment, the average percentage of
matching positions is 26%

```



****



## 实验六、遗传密码

[TOC]

### 一、将DNA翻译成蛋白质

```perl
#!/usr/bin/perl 

use strict;
use warnings;


my $dna = 'CGACGTCTTCGTACGGGACTAGCTCGTGTCGGTCGC';
my $protein = '';
my $codon;

for(my $i=0; $i < (length($dna) - 2) ; $i +=3) {
$codon = substr($dna,$i,3);
$protein .= codon2aa($codon);
}
print "I translated the DNA\n\n$dna\n\n into the protein\n\n$protein\n\n";

# cond2dd 将密码子翻译成氨基酸
sub codon2aa {
my($codon) = @_;
$codon = uc $codon;
my(%genetic_code) = (

'TCA' => 'S', # Serine
'TCC' => 'S', # Serine
'TCG' => 'S', # Serine
'TCT' => 'S', # Serine
'TTC' => 'F', # Phenylalanine
'TTT' => 'F', # Phenylalanine
'TTA' => 'L', # Leucine
'TTG' => 'L', # Leucine
'TAC' => 'Y', # Tyrosine
'TAT' => 'Y', # Tyrosine
'TAA' => '_', # Stop
'TAG' => '_', # Stop
'TGC' => 'C', # Cysteine
'TGT' => 'C', # Cysteine
'TGA' => '_', # Stop
'TGG' => 'W', # Tryptophan
'CTA' => 'L', # Leucine
'CTC' => 'L', # Leucine
'CTG' => 'L', # Leucine
'CTT' => 'L', # Leucine
'CCA' => 'P', # Proline
'CCC' => 'P', # Proline
'CCG' => 'P', # Proline
'CCT' => 'P', # Proline
'CAC' => 'H', # Histidine
'CAT' => 'H', # Histidine
'CAA' => 'Q', # Glutamine
'CAG' => 'Q', # Glutamine
'CGA' => 'R', # Arginine
'CGC' => 'R', # Arginine
'CGG' => 'R', # Arginine
'CGT' => 'R', # Arginine
'ATA' => 'I', # Isoleucine
'ATC' => 'I', # Isoleucine
'ATT' => 'I', # Isoleucine
'ATG' => 'M', # Methionine
'ACA' => 'T', # Threonine
'ACC' => 'T', # Threonine
'ACG' => 'T', # Threonine
'ACT' => 'T', # Threonine
'AAC' => 'N', # Asparagine
'AAT' => 'N', # Asparagine
'AAA' => 'K', # Lysine
'AAG' => 'K', # Lysine
'AGC' => 'S', # Serine
'AGT' => 'S', # Serine
'AGA' => 'R', # Arginine
'AGG' => 'R', # Arginine
'GTA' => 'V', # Valine
'GTC' => 'V', # Valine
'GTG' => 'V', # Valine
'GTT' => 'V', # Valine
'GCA' => 'A', # Alanine
'GCC' => 'A', # Alanine
'GCG' => 'A', # Alanine
'GCT' => 'A', # Alanine
'GAC' => 'D', # Aspartic Acid
'GAT' => 'D', # Aspartic Acid
'GAA' => 'E', # Glutamic Acid
'GAG' => 'E', # Glutamic Acid
'GGA' => 'G', # Glycine
'GGC' => 'G', # Glycine
'GGG' => 'G', # Glycine
'GGT' => 'G', # Glycine
);
if(exists $genetic_code{$codon}) {
return $genetic_code{$codon};
}else{
print STDERR "Bad codon \"$codon\"!!\n";
exit;
}
}
exit;
```

结果：

```shell
I translated the DNA

CGACGTCTTCGTACGGGACTAGCTCGTGTCGGTCGC

into the protein

RRLRTGLARVGR
```

### 二、读取FASTA文件

```perl
#!/usr/bin/perl -w

use strict;
use warnings;
use Biosub;

my @file_data = ( );
my $dna = '';
@file_data = get_file_data("NM_021964.fasta");
$dna = extract_sequence_from_fasta_data(@file_data);
print_sequence($dna, 25);

# get_file_data 获取fasta文件中的数据
sub get_file_data {
my($filename) = @_;
use strict;
use warnings;
my @filedata = ( );
unless( open(GET_FILE_DATA, $filename) ) {
print STDERR "Cannot open file \"$filename\"\n\n";
exit;
}
@filedata = <GET_FILE_DATA>;
close GET_FILE_DATA;
return @filedata;
}

# extract_sequence_from_fasta_data 提取fasta中的序列信息
sub extract_sequence_from_fasta_data {
my(@fasta_file_data) = @_;
use strict; use warnings;
my $sequence = ''; 
foreach my $line (@fasta_file_data) {
if ($line =~ /^\s*$/) { next;        # 跳过无用的信息
} elsif($line =~ /^\s*#/) { next;
} elsif($line =~ /^>/) { next;
} else { $sequence .= $line; }
}
$sequence =~ s/\s//g; return $sequence;
}

# print_sequence 将序列格式化输出
sub print_sequence {
my($sequence, $length) = @_;
use strict;
use warnings;

for ( my $pos = 0 ; $pos < length($sequence) ; $pos += $length ) {
print substr($sequence, $pos, $length), "\n";

}
}

```

结果：

```
GGCGACCGCGGCGGCGCTCTAGCTGCGGCATGTCTGCGTCTCTACTGCTCTGGGAGGAGGAAGAGAAGGA
GGAAGAGGAGGAGGAGGAGGAGGGGGAGGAAGAGGAGAAAGGCGCAGGGGTGGGAGCTGTTGCCGAAGCT
GCCACAGCAAAAGTTCTCCCCCCTCCCCCCTTCCCCTCCTCTCAAGGCCCCTAGAAAGGTTGGAGCTGCC
GCCGCCTGCAGTCGGTGACCGCGCGACTCGGCGCCCGCCCGCGGATAGAGGGAGGAATCAGCAGCTTGGA
AATTCAAGCACGTGATCTGGCGGGATGGGCGTTTGCCTAACGTATTTAATGGAGGAATCGGATGGCATAA
GTGATTAAGGTGGTATTGAGGATTTCTGAAGCCTATGAAAGGTAGAAACTCAACCATGATTTCTTTTTCA
ACTCTACAGCATTCCTTTCCTTGAAGTCTTCGTTTTTACCTTAGTCTCGGGCAGTTATACTTAAGCATGA
ACATTGACGACAAACTGGAAGGATTGTTTCTTAAATGTGGCGGCATAGACGAAATGCAGTCTTCCAGGAC
AATGGTTGTAATGGGTGGAGTGTCTGGCCAGTCTACTGTGTCTGGAGAGCTACAGGATTCAGTACTTCAA
GATCGAAGTATGCCTCACCAGGAGATCCTTGCTGCAGATGAAGTGTTACAAGAAAGTGAAATGAGACAAC
AGGATATGATATCACATGATGAACTCATGGTCCATGAGGAGACAGTGAAAAATGATGAAGAGCAGATGGA
AACACATGAAAGACTTCCTCAAGGACTACAGTATGCACTTAATGTCCCTATAAGCGTAAAGCAGGAAATT
ACTTTTACTGATGTATCTGAGCAACTGATGAGAGACAAAAAACAAATCAGAGAGCCAGTAGACTTACAGA
...
```



### 三、翻译阅读框

```perl
#!/usr/bin/perl

use strict;
use warnings;
use Biosub;
my @file_data = ( );
my $dna = '';
my $revcom = '';
my $protein = '';

@file_data = get_file_data("NM_021964.fasta");
# DNA的一条链进行阅读框翻译
$dna = extract_sequence_from_fasta_data(@file_data);
print "\n -------Reading Frame 1--------\n\n";
$protein = translate_frame($dna, 1);
print_sequence($protein, 70);
print "\n -------Reading Frame 2--------\n\n";
$protein = translate_frame($dna, 2);
print_sequence($protein, 70);
print "\n -------Reading Frame 3--------\n\n";
$protein = translate_frame($dna, 3);
print_sequence($protein, 70);

# 取DNA反向互补序列，进行阅读框翻译
$revcom = revcom($dna);
print "\n -------Reading Frame 4--------\n\n";
$protein = translate_frame($revcom, 1);
print_sequence($protein, 70);
print "\n -------Reading Frame 5--------\n\n";
$protein = translate_frame($revcom, 2);
print_sequence($protein, 70);
print "\n -------Reading Frame 6--------\n\n";
$protein = translate_frame($revcom, 3);
print_sequence($protein, 70);


```

结果：

```

 -------Reading Frame 1--------

GDRGGALAAACLRLYCSGRRKRRRKRRRRRRGRKRRKAQGWELLPKLPQQKFSPLPPSPPLKAPRKVGAA
AACSR_PRDSAPARG_REESAAWKFKHVIWRDGRLPNVFNGGIGWHK_LRWY_GFLKPMKGRNSTMISFS
TLQHSFP_SLRFYLSLGQLYLSM

 -------Reading Frame 2--------

ATAAAL_LRHVCVSTALGGGREGGRGGGGGGGGRGERRRGGSCCRSCHSKSSPPSPLPLLSRPLERLELP
PPAVGDRATRRPPADRGRNQQLGNSST_SGGMGVCLTYLMEESDGISD_GGIEDF_SL_KVETQP_FLFQ
LYSIPFLEVFVFTLVSGSYT_A_

 -------Reading Frame 3--------

RPRRRSSCGMSASLLLWEEEEKEEEEEEEEGEEEEKGAGVGAVAEAATAKVLPPPPFPSSQGP_KGWSCR
RLQSVTARLGARPRIEGGISSLEIQARDLAGWAFA_RI_WRNRMA_VIKVVLRISEAYER_KLNHDFFFN
STAFLSLKSSFLP_SRAVILKH

 -------Reading Frame 4--------

PLAPPRDRRRTDAEMTRPSSFSSSFSSSSSSPSFSSFRVPTLDNGFDGVVFKRGEGGRGGEFRGSFQPRR
RRTSATGALSRGRAPISLLSRRTFKFVH_TALPANGLHKLPP_PTVFTNSTITPKDFGYFPSLSWY_RKS
_DVVRKGTSEAKMESEPVNMNSY

 -------Reading Frame 5--------

RWRRREIDAVQTQR_RDPPPSLPPSPPPPPPPPSPLSASPPSTTASTVSFSRGGRGEGEESSGDLSNLDG
GGRQPLAR_AAGGRLSPSLVVEPLSSCTRPPYPQTDCINYLLSLPYSLIPP_LLKTSDTFHL_VGTKEKV
EMS_GKELQKQKWNQSPSI_IRT

 -------Reading Frame 6--------

AGAAARSTPYRRRDDETLLLLFLLLLLLLLPLLLLFPRPHPRQRLRRCRFQEGGGGKGRRVPGIFPTSTA
ADVSHWRAEPRAGAYLPP_SSNL_VRALDRPTRKRIA_ITSLAYRIH_FHHNS_RLRILSIFELVLKKKL
RCRKERNFRSKNGIRARQYEFV

```

---



## 实验七、限制酶图谱

[TOC]



### 一、制作图谱

```perl
#!/usr/bin/perl

use strict;
use warnings;
use Biosub;

my %rebase_hash = ();
my @file_data = ();
my $query = '';
my $dna = '';
my $recognition_site = '';
my $regexp = '';
my @locations = ();
@file_data = get_file_data("NM_021964.fasta");  # 打开DNA序列文件
$dna = extract_sequence_from_fasta_data(@file_data);
%rebase_hash = parseREBASE('bionet');

do {
print "Search for what restriction site
for (or quit)?: ";
$query = <STDIN>;
chomp $query;

if ( $query =~ /^\s*$/ ) {
exit;
}
if ( exists $rebase_hash{$query} ) {
( $recognition_site, $regexp ) =split( " ", $rebase_hash{$query} );
@locations = match_positions( $regexp, $dna );
if (@locations) {
print "Searching for $query $recognition_site $regexp\n";
print "A restriction site for $query at locations:\n";
print join( " ", @locations ), "\n";
}
else {
print "A restriction enzyme $query is
not in the DNA:\n";
}
}
print "\n";
} until ( $query =~ /quit/ );
exit;
```

结果：

```shell
Search for what restriction enzyme (or quit)?: AceI
Searching for AceI G^CWGC GC[AT]GC
A restriction site for AceI at locations:
54 94 582 660 696 702 840 855 957
Search for what restriction enzyme (or quit)?: AccII
Searching for AccII CG^CG CGCG
A restriction site for AccII at locations:
181
Search for what restriction enzyme (or quit)?: AaeI
A restriction site for AaeI is not in the DNA:
Search for what restriction enzyme (or quit)?: quit
```







### 附：包含之前所有相关子程序的模块 Biosub

```perl
#!/usr/bin/perl

use warnings;
use strict;

# 产生随机位置
sub randomposition {
    my ($string) = @_;
    return int( rand( length($string) ) );
}

# 产生随机碱基
sub randomnucleotide {
    my (@nucleotides) = ( 'A', 'C', 'G', 'T' );
    return randomelement(@nucleotides);
}

# 产生随机长度
sub randomlength {
    my ( $minlength, $maxlength ) = @_;
    return ( int( rand( $maxlength - $minlength + 1 ) ) + $minlength );
}

# 产生一条随机DNA序列
sub make_random_DNA {
    my ($length) = @_;
    my $dna;
    for ( my $i = 0 ; $i < $length ; ++$i ) {
        $dna .= randomnucleotide();
    }
    return $dna;
}

# 产生指定数目多条随机DNA序列
sub make_random_DNA_set {
    my ( $minimum_length, $maximum_length, $size_of_set ) = @_;
    my $length;
    my $dna;
    my @set;

    for ( my $i = 0 ; $i < $size_of_set ; ++$i ) {
        $length = randomlength( $minimum_length, $maximum_length );
        $dna = make_random_DNA($length);
        push( @set, $dna );
    }
    return @set;
}

# 计算两条序列比对后，相同位置的一致率
sub matching_percentage {
    my ( $string1, $string2 ) = @_;
    my ($length) = length($string1);
    my ($position);
    my ($count) = 0;

    for ( $position = 0 ; $position < $length ; ++$position ) {
        if (
            substr( $string1, $position, 1 ) eq
            substr( $string2, $position, 1 ) )
        {
            ++$count;
        }
    }
    return $count / $length;
}

# 随机从数组产生一个元素
sub randomelement {
    my (@array) = @_;
    return $array[ rand @array ];
}

# 碱基突变过程
sub mutate {
    my ($dna)      = @_;
    my ($position) = randomposition($dna);    # 获取随机突变位置
    my ($newbase)  = randomnucleotide();      # 获取要突变成为的碱基
    substr( $dna, $position, 1, $newbase )
      ;             # 将该位置的碱基替换为突变后的碱基
    return $dna;    # 将突变后的DNA序列传递回去
}

# DNA翻译为蛋白，密码子对应氨基酸
sub codon2aa {
    my ($codon) = @_;
    $codon = uc $codon;
    my (%genetic_code) = (

        'TCA' => 'S',    # Serine
        'TCC' => 'S',    # Serine
        'TCG' => 'S',    # Serine
        'TCT' => 'S',    # Serine
        'TTC' => 'F',    # Phenylalanine
        'TTT' => 'F',    # Phenylalanine
        'TTA' => 'L',    # Leucine
        'TTG' => 'L',    # Leucine
        'TAC' => 'Y',    # Tyrosine
        'TAT' => 'Y',    # Tyrosine
        'TAA' => '_',    # Stop
        'TAG' => '_',    # Stop
        'TGC' => 'C',    # Cysteine
        'TGT' => 'C',    # Cysteine
        'TGA' => '_',    # Stop
        'TGG' => 'W',    # Tryptophan
        'CTA' => 'L',    # Leucine
        'CTC' => 'L',    # Leucine
        'CTG' => 'L',    # Leucine
        'CTT' => 'L',    # Leucine
        'CCA' => 'P',    # Proline
        'CCC' => 'P',    # Proline
        'CCG' => 'P',    # Proline
        'CCT' => 'P',    # Proline
        'CAC' => 'H',    # Histidine
        'CAT' => 'H',    # Histidine
        'CAA' => 'Q',    # Glutamine
        'CAG' => 'Q',    # Glutamine
        'CGA' => 'R',    # Arginine
        'CGC' => 'R',    # Arginine
        'CGG' => 'R',    # Arginine
        'CGT' => 'R',    # Arginine
        'ATA' => 'I',    # Isoleucine
        'ATC' => 'I',    # Isoleucine
        'ATT' => 'I',    # Isoleucine
        'ATG' => 'M',    # Methionine
        'ACA' => 'T',    # Threonine
        'ACC' => 'T',    # Threonine
        'ACG' => 'T',    # Threonine
        'ACT' => 'T',    # Threonine
        'AAC' => 'N',    # Asparagine
        'AAT' => 'N',    # Asparagine
        'AAA' => 'K',    # Lysine
        'AAG' => 'K',    # Lysine
        'AGC' => 'S',    # Serine
        'AGT' => 'S',    # Serine
        'AGA' => 'R',    # Arginine
        'AGG' => 'R',    # Arginine
        'GTA' => 'V',    # Valine
        'GTC' => 'V',    # Valine
        'GTG' => 'V',    # Valine
        'GTT' => 'V',    # Valine
        'GCA' => 'A',    # Alanine
        'GCC' => 'A',    # Alanine
        'GCG' => 'A',    # Alanine
        'GCT' => 'A',    # Alanine
        'GAC' => 'D',    # Aspartic Acid
        'GAT' => 'D',    # Aspartic Acid
        'GAA' => 'E',    # Glutamic Acid
        'GAG' => 'E',    # Glutamic Acid
        'GGA' => 'G',    # Glycine
        'GGC' => 'G',    # Glycine
        'GGG' => 'G',    # Glycine
        'GGT' => 'G',    # Glycine
    );
    if ( exists $genetic_code{$codon} ) {
        return $genetic_code{$codon};
    }
    else {
        print STDERR "Bad codon \"$codon\"!!\n";
        exit;
    }
}

# 将DNA翻译成多肽
sub dna2peptide {
    my ($dna) = @_;
    use strict;
    use warnings;
    my $protein = '';
    for ( my $i = 0 ; $i < ( length($dna) - 2 ) ; $i += 3 ) {
        $protein .= codon2aa( substr( $dna, $i, 3 ) );
    }
    return $protein;
}

# 打开并读取fasta文件相关子程序
# 获取fasta文件所有数据
sub get_file_data {
    my ($filename) = @_;
    use strict;
    use warnings;
    my @filedata = ();
    unless ( open( GET_FILE_DATA, $filename ) ) {
        print STDERR "Cannot open file \"$filename\"\n\n";
        exit;
    }
    @filedata = <GET_FILE_DATA>;
    close GET_FILE_DATA;
    return @filedata;
}

# 跳过非序列信息，只提取序列信息
sub extract_sequence_from_fasta_data {
    my (@fasta_file_data) = @_;
    use strict;
    use warnings;
    my $sequence = '';
    foreach my $line (@fasta_file_data) {
        if ( $line =~ /^\s*$/ ) {
            next;
        }
        elsif ( $line =~ /^\s*#/ ) {
            next;
        }
        elsif ( $line =~ /^>/ ) {
            next;
        }
        else { $sequence .= $line; }
    }
    $sequence =~ s/\s//g;
    return $sequence;
}

# 依次输出fasta文件中的序列信息
sub print_sequence {
    my ( $sequence, $length ) = @_;
    use strict;
    use warnings;

    for ( my $pos = 0 ; $pos < length($sequence) ; $pos += $length ) {
        print substr( $sequence, $pos, $length ), "\n";
    }
}

# 翻译DNA阅读框相关子程序
# 翻译阅读框
sub translate_frame {
    my ( $seq, $start, $end ) = @_;
    unless ($end) {
        $end = length($seq);
    }
    return dna2peptide( substr( $seq, $start - 1, $end - $start + 1 ) );
}

# 取反向互补序列
sub revcom {
    my ($dna)    = @_;
    my ($revcom) = reverse($dna);
    $revcom =~ tr/ACGTacgt/TGCAtgca/;
    return $revcom;
}

# 在DNA中查询并返回匹配位置
sub match_positions {
    my ( $regexp, $sequence ) = @_;
    use strict;
    my @positions = ();
    while ( $sequence =~ /$regexp/ig ) {
        push( @positions, pos($sequence) - length($&) + 1 );
    }
    return @positions;
}

# 限制酶图谱相关子程序
# 将REBASE文档中模糊的IUB代码翻译成正则表达式
sub IUB_to_regexp {
    my ($iub)               = @_;
    my $regular_expression  = '';
    my %iub2character_class = (
        A => 'A',
        C => 'C',
        G => 'G',
        T => 'T',
        R => '[GA]',
        Y => '[CT]',
        M => '[AC]',
        K => '[GT]',
        S => '[GC]',
        W => '[AT]',
        B => '[CGT]',
        D => '[AGT]',
        H => '[ACT]',
        V => '[ACG]',
        N => '[ACGT]',
    );
    $iub =~ s/\^//g;
    for ( my $i = 0 ; $i < length($iub) ; ++$i ) {
        $regular_expression .= $iub2character_class{ substr( $iub, $i, 1 ) };
    }
    return $regular_expression;
}

# 解析REBASE数据文件
sub parseREBASE {
    my ($rebasefile) = @_;
    use strict;
    use warnings;
    my %rebase_hash = ();
    my $name;
    my $site;
    my $regexp;
    my $rebase_filehandle = open_file($rebasefile);

    while (<$rebase_filehandle>) {
        ( 1 .. /Rich Roberts/ ) and next;
        /^\s*$/ and next;
        my @fields = split( " ", $_ );
        $name               = shift @fields;
        $site               = pop @fields;
        $regexp             = IUB_to_regexp($site);
        $rebase_hash{$name} = "$site $regexp";
    }
    return %rebase_hash;
}

# 打开文件(用于REBASE中)
sub open_file {
    my ($filename) = @_;
    my $fh;
    unless ( open( $fh, $filename ) ) {
        print "Cannot open file $filename\n";
        exit;
    }
    return $fh;
}
1;

```









