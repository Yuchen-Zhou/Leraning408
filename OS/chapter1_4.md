## 1.4 操作系统

1.   **分层法**

     分层法是将操作系统分为若干层，最底层为硬件，最高层为用户接口，每层只能调用紧邻它的底层的功能和服务，如同一个鸡蛋。

     优点：

     -   便于系统的调试和验证，简化了系统的设计和实现。
     -   易扩充和易维护。

     问题：

     -   合理定义各层比较困难
     -   效率较差

2.   **模块化**

     模块化是将操作系统按功能划分为若干个具有一定独立性的模块。每个模块具有某方面的管理功能，并规定好各模块间的接口，使各模块之间能够通过接口进行通信。

     模块划分时，需要考虑到模块的独立性问题，模块的独立性越高，各模块间的交互就越少，系统的结构也就越清晰。衡量模块独立性有两个标准：

     -   内聚性，模块内部各部分间联系的紧密程度。内聚性越高，模块独立性越好
     -   耦合度，模块间相互联系和相互影响的程度。耦合度越低，模块独立性越好

     优点：

     -   提高了操作系统设计的正确性、可理解性和维护性
     -   增强了操作系统的可适应性
     -   加速了操作系统的开发过程

     缺点：

     -   模块间的接口规定很满足对接口的实际需求
     -   各模块设计者齐头并进，每个决定无法建立在上一个已验证的正确决定的基础上，因此无法找到一个可靠的决定顺序

3.   **宏内核**

     操作系统的内核架构来看，分为宏内核和微内核

     宏内核，也称单内核或大内核，是指将系统的主要功能模块都作为一个紧密联系的整体运行在核心态，从而为用户程序提供高性能的系统服务。各个模块之间共享信息，能有效利用相互之间的有效特性，具有无可比拟的性能优势。

4.   **微内核**

     **微内核的基本概念**

     微内核架构，是指将内核中最基本的功能保留在内核，而将那些不需要在核心态执行的功能移到用户态执行，从而降低内核的设计复杂性。

     微内核结构将操作系统划分为两大部分：微内核和多个服务器。微内核是精心设计的、能实现操作系统最基本核心功能的小型内核，通常包括：

     -   与硬件处理紧密相关的部分
     -   一些较基本的功能
     -   客户和服务器之间的通信

     操作系统中的绝大部分功能都放在微内核外的一组服务器中实现，如用于提供对进程进行管理的进程服务器、提供虚拟存储器管理功能的虚拟存储器服务器等，它们都是作为进程来实现的，运行在用户态、客户与服务器之间是借助微内核提供的消息传递机制来实现交互的。

​		**微内核的基本功能**

  -    进程（线程）管理。进程（线程）之间的通信功能是微内核OS最基本的功能，此外还有进程的切换、进程的调度，以及多处理机之间的同步等功能，都应该放入微内核。

  -    低级存储器管理。在微内核中，只配置最基本的低级存储器管理机制，如用于实现将逻辑地址变换为物理地址等的页表机制，这一部分是依赖于硬件的，因此放入微内核。

  -    中断和陷入处理。微内核OS将与硬件紧密相关的一小部分放入微内核，此时微内核的主要功能是捕获所发生的中断和陷入事件，并进行中断响应处理，在识别中断或陷入的事件后，再发送给相关的服务器来处理，故中断和陷入处理也应放入微内核

       

       **微内核的特点**

  -    扩展性和灵活性

  -    可靠性和安全性

  -    可移植性

  -    分布式计算

微内核的主要问题是性能问题，需要频繁地在用户态和核心态之间切换，操作系统的执行开销偏大。

5.   外核

     对机器进行分区，给每个用户整个资源的一个子集。在底层中，外核程序运行在内核态中，任务是为虚拟机分配资源，并检查使用这些资源的企图，以确保没有机器会使用他人的资源。

     优点：减少了映射层、将多道程序与用户操作系统代码加以分离，而且相应的负载并不重。

     