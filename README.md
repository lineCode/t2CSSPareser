# t2CSSPareser

使用Flex+Bison完成CSS词法分析与语法分析工作，具体BNF是参考W3C中CSS2.0标准实现(实现了部分CSS3.0)。

## 依赖项说明
1.[Flex](http://flex.sourceforge.net/) 2.5.35

2.[Bison](https://www.gnu.org/software/bison/) 2.4.1

(Windows版本可以使用[MinGW](http://www.mingw.org/)，OSX为自带)

3.[Graphviz](http://www.graphviz.org/)(可选)，用于可视化生成AST树

## 构建说明
1.自带Makefile，自带demo.css无需其他平台依赖项

2.不使用g++ 而使用Visual Studio编译时可能会遇到```unistd.h```无法找到的问题，目前的解决方案可以是直接在VS的include目录下添加

具体操作可以参见[在VC下如何使用头文件unistd.h](http://weilihero.blog.163.com/blog/static/13411039520109218831848/)

## 使用说明
1.目前支持CSS2.0大部分特性，正如demo.css中显示的

2.所有数值不带单位，例如
```css
/* 已知错误 */
font-size: 80;
/* font-size: 80px; */

```
此处一旦数值带有单位将会发生```不可预测错误```。

3.AST基本数据类型已经在```t2CSSNode.hpp```中显示，其中可视化AST可以调用```printAsDot()```方法。

4.目前语法错误无法检测具体错误类型，只能显示```Error: syntax error.```。

5.目前规则不能为空，例如
```css
/* Syntax error */
hello.a{}
```
在t2CSSParser中会被认为有语法错误,目前的解决办法是手工直接删除空规则，等待版本。

## 可视化AST
此为给出的demo.css生成的AST具体样式
![AST](https://raw.githubusercontent.com/BentleyBlanks/t2CSSPareser/master/AST/AST.png)


## 关于作者
```cpp
int 官某某 = "Bingo";

char[] 个人博客 = "http://bentleyblanks.github.io";
```
