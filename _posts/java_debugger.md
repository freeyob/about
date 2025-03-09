> 为什么要写这个文档？？
> 1. 学习Debugger的设计
> 2. 实现一个ZED java debugger（如果需要的话，我就继续写，如果不需要，先暂停）
> 3. 简历上多个亮眼的·项目经历
> 4. 写Zed插件是一个学习Rust的好方法

下一步
> 1.阅读vscode debugger 开发文档
> 2. 阅读DAP协议
> 3. 阅读vscode debugger Java插件源码
> 4. 阅读Java DAP插件源码
# Java Debugger分析

最近发现一个很不错的编辑器Zed，编辑体验很不错。但是他的Debug的功能还在开发中。
想到一个问题：IDE是怎么支持Debug的。用Java比较多，就从Java入手开始分析。

## Java Debugger 是什么？

Java Debugger 是一个用于调试 Java 程序的工具。它允许程序员在程序运行时暂停程序的执行，查看程序的状态，以及查看程序的变量值。
Java Debugger 通常包括以下功能：
- 设置断点：在程序中设置断点，当程序执行到断点时，程序会暂停执行。
- 单步执行：一次执行一行代码，可以查看程序的执行过程。
- 查看变量值：可以查看程序中变量的值。

## Java Debugger 怎么做到的？

1. 能力。要在运行的时候设置断点和查看变量，只有虚拟机可以做到。[接口文档](https://docs.oracle.com/javase/8/docs/jdk/api/jpda/jdi/)
2. 操作界面。vscode和ecplise对应有debug界面。如下图。好像还有专门做这个的程序。
3. 控制。能力和操作界面抽象不一样，要解决能力和操作界面结合起来的问题。有个专门的协议DAP专门来解决这个问题。[DAP协议](https://microsoft.github.io/debug-adapter-protocol/)。
并且这个逻辑是语言相关的，写在IDE里不合适，假如每个编程语言都写进去，IDE就臃肿了。独立出来还能让其他IDE复用。
<details>
## 深入分析VSCode怎么支持Java Debugger的
看图![vscode debugger 架构图](https://code.visualstudio.com/assets/api/extension-guides/debugger-extension/debug-arch1.png)
## 那么Zed如何才能支持Java Debugger呢？需要我做点什么吗。
  1. 首先要支持DAP协议，这个是通用的，不用关心具体语言。
  2. 然后要支持Java的JDI接口，这个是Java特有的。
  3. 最后要做一个操作界面，这个是IDE特有的。
</details>
