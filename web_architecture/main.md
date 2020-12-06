# web 架构

所谓 web 就是 website 的简称，中文翻译就是网站，即网络中的一个站点（节点）。而这个网络就是 WWW（world wide web）即万维网。

而 WWW 是建立在 Internet （计算机互联网）之上的一个应用层范式，他不是一个具体的协议，而是包含众多技术协议的一个协议簇。他最开始诞生的目的很简单，就是传输文本。

但是这个文本可不是普通的文本（plain text），因为真正的文本比如论文和报告，其中含有格式、图片、图表等内容。而包含这些内容的文本，就是所谓的超文本（hyper text）。书写这个超文本的语言，就是超文本标记语言（HTML）。依托于 Internet 传输文本的具体协议，就是超文本传输协议（HTTP）。

为了阅读超文本，用户需要一个客户端，这个客户端，就是传说中的浏览器。浏览器的功能顾名思义，即浏览超文本的机器。依托于互联网，他还打包了通过统一资源定位符（URI，俗称网址），取回超文本的功能。

所以 WWW 是干什么的呢，就是依托于计算机互联网（Internet），传递超文本的应用范式。用户依据统一资源定位符（URI）通过浏览器取回超文本。

以上就是 WWW 最开始的样子，我先不讲后期出现的单页 APP （SPA），先搭建一个文本服务器并通过浏览器访问的实验，来开启对 Web 的探索。

## 盘古开天地：静态网站

首先我们在本地生成一些静态资源

```bash
# 创建一个文件夹
mkdir my_web
# 进入刚才创建的文件夹
cd my_web
# 生成一个简单文本
touch index.txt
# 写入内容
echo 'hello world' > index.txt
```

```
my_web
└── index.txt

0 directories, 1 file
```

通过上面的命令，我们得到了上面这个`my_web`文件夹，里面有一个文本，里面写了一句`hello world`。下面我要通过一个服务器把这个文件夹变成一个网站，让所有人都能通过 `URI` 和浏览器查看。

服务器这个词在不同的语境下不一样，如果是在现实世界，他就是一台运行服务器软件的电脑。如果在电脑内部，他就是一个服务器软件。服务器软件有多种多样，下面我要用到的是 python3 自带的静态资源服务器。

进入到刚才的文件夹 `my_web` 中运行命令：

```bash
python -m http.server
```

之后 shell 就会被刚才的程序阻断，之后输出如下提示

```
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
```

对于`http://0.0.0.0:8000/`就是所谓的`URI`，其中的 `0.0.0.0` 是ip地址，他是网络层协议（IP）规定的。`0.0.0.0` 他是一个特殊的 ip 地址，不能在实际中使用，这里用它的目的是在启动服务器的时候省略本机的 ip 地址，让服务器软件自己找自己的 ip 。而 `8000` 是端口号的意思，他是传输层协议（TCP/IP）规定的，而最前面的 `http`，就是我们刚才提到的协议名称，用来指定具体的应用层协议。

之后我们打开浏览器，在地址栏中输入 `http://127.0.0.1:8000/`，就能浏览到刚才的文本了。读者可能会想，这也不是超文本啊，目前来说的确不是，但其实超文本传输协议的功能非常多样，文件，文本（普通文本和超文本）都可以传输。超文本都能传输，传输普通文本不就是小意思吗。为了控制教程的复杂程度，HTML 这里先不介绍。

这其中的 `127.0.0.1` 即为本机的回环地址，域名为 `localhost`，你也可以输入 `http://localhost:8000/`。输入这个地址并不会访问别的机器，而是会访问自己的机器。你不能通过这个地址访问别人，别人也不能通过这个地址访问你。所以每个电脑访问这个地址都会得到不一样的结果。如果你没开启服务器，就什么都访问不到。

总体而言，ip 地址是用来标注一个服务器的（和服务器一一对应），而端口号就是用来标记这个机器上的进程（和具体进程一一对应）。而`ip:port`的格式加到一起，就是一个 socket （套接字），这个是传输层（TCP/UDP）协议中确定的内容，我们的 HTTP 协议是应用层协议，他依托于传输层，所以在套接字的部分，当然还是一样的。

至于域名，他就是 ip 地址的别名，通过域名服务器（DNS） 进行翻译。

上面这些内容，是比较粗浅的介绍，我在后面的内容中还会仔细介绍，看得一知半解也没关系，大概看一下，可以先略过。

## 谈谈基础：进程与进程间通信

### 进程模型

如果你深入研究过电脑，你应该会理解什么是进程。从定义上来讲，进程就是**程序的一次执行**。所谓程序，就是指令和数据的集合。

你写一个程序出来，把他编译成一个可执行文件。他目前的位置是在硬盘里的，他是死的。之后你把他双击执行，CPU 就会把他的指令和数据装在到内存之中，之后从内存中读取指令，让他在 CPU中执行，他就变成了一个进程。

我们接上一章，刚才我们不是运行了一个 python 静态资源服务器吗，我们就看看这个进程。

执行命令：

```bash
ps
```

会得到如下输出

```
  PID TTY           TIME CMD
53688 ttys006    0:00.32 python -m http.server
# 其他输出省略
```

`16751` 就是他的进程号，这个进程号是对于机器内部的编号，而我们刚才说的端口号`8000`，是这个进程在网络中的编号，他们本质上是一回事，都用来唯一标注某个机器上的一个进程。

### 本地进程之间通信

对于学过编程的人，应该都不难理解进程模型，毕竟他就是**程序的一次执行**。但是可能很多人学了很多年编程都没有接触过进程间通信。

进程间通信在实际的开发之中非常常见，无论是本地的应用，还是网络应用，都依托与这个功能。**网络请求本质上也是进程之间通信**。网络通信的步太远，容易扯到蛋，我们先看看简单一点的本地通信。

本地进程间通信的方法多种多样，我就举一个我写过的项目里用过的 Linux 命名管道（FIFO）的形式。

后台服务程序：**daemon.cpp**

```cpp
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <limits.h>
#include <string.h>

#include <iostream>

#include "config.h"
#include "file_system.h"



//read the fifo
//daemon
int main()
{
    int C_to_D_id, D_to_C_id, file_id;
    char buffer[PIPE_BUF+1];            //4096+1

    mkfifo(C_to_D_name, 0777);
    mkfifo(D_to_C_name, 0777);
    
    //...
}

```

重点关注 24、25行，我创建了两个命名管道。

客户端程序：**client.cpp**

```cpp
//
// Created by ZIdongFang on 2019-06-01.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <limits.h>
#include <string.h>


#include <iostream>

#include "config.h"
#include "mystring.h"


using namespace std;

int main()
{
    int C_to_D_id, D_to_C_id;
    char buffer[PIPE_BUF+1];
    printf("welcome to use fsh (๑•̀ㅂ•́)و✧\n\n");
    C_to_D_id = open(C_to_D_name, O_WRONLY);
    D_to_C_id = open(D_to_C_name, O_RDONLY);
    // ...
}
```

重点关注 28、29行，我打开了两个命名管道。在 UNIX 系的操作系统中，有一个一切皆文件的思想，即所有的硬件，软件，都可以通过文件读取的方式来访问，命名管道也不例外。

什么是命名管道呢，他本质上就是一个先进先出的消息队列，一方面向其中填入数据，另一方从中读取数据。大致就是这么一个简单的过程。

在现代软件开发中，我们有非常多的成熟的消息队列解决方案，但是最基础的思想，都是这样的。如果好奇我具体是怎么使用消息队列的，可以看完整的项目代码。关注我上面列的两个文件就好了，其他具体实现不在本文讨论范围之内。

完整项目代码：

[github/bjfu_os_final_design](https://github.com/quaeast/os_final_design)

## 洪荒时代：Socket

Socket 是 **TCP/IP 协议具体实现，用于完成远端进程之间通信。**

所谓 Socket 中文翻译就是套接字，字面意思指的是 `ip:port` 这两个部分接到一起。但实际含义是，对于 TCP/IP 协议在 BSD UNIX（Berkeley Software Distribut） 操作系统上的具体实现。最早是由 UC Berkeley 的老师和同学实现，发行于 BSD UNIX 之上。因为起步较早，影响很广，所以后期 Windows，Linux 以及其他版本的 UNIX 操作系统的 TCP/IP 实现也沿用了这个名字。但其实严格来讲他们不是一回事。总之，一提到 Socket 你就知道他是 TCP/IP 协议具体实现，用于完成远端进程之间通信就可以了。

下面我们用基础的方式调用 Socket 来实现一个基本的进程之间通信。

服务端代码 `server.py`:

```python
import socket
ip_port = ('0.0.0.00', 5000)

s = socket.socket()
s.bind(ip_port)
s.listen(5)

while True:

    conn, addr = s.accept()

    while True:

        try:

            recv_data = conn.recv(1024)
            if len(recv_data) == 0:
                break

            send_data = recv_data.upper()
            print(send_data)

            conn.send(send_data)

        except Exception:
            break

    conn.close()
```

关注上面代码的第二行，作为服务端，制定自己的 ip 地址和端口号。

客户端代码 `client.py` ：

```python
import socket

# ip_port = ('127.0.0.1', 9)
ip_port = ('39.96.177.143', 5000)
s = socket.socket()
s.connect(ip_port)

while True:

    send_data = input(">>: ").strip()
    if len(send_data) == 0:
        continue

    s.send(bytes(send_data, encoding='utf8'))

    if send_data == 'exit':
        break

    recv_data = s.recv(1024)
    print(str(recv_data, encoding='utf8'))

s.close()
```

关注代码的第四行，制定服务端的 ip 和端口号，这里填你自己刚才运行起来的服务器进程的 ip 和端口号即可。我们可以通过修改参数太选择 TCP/UDP 协议，这些对于理解进程之间通信并不重要，此处略过。

上面两段代码都运行起来之后，我们在客户端这边输入一个内容，就能在远端的服务器收到。这就是最简单的远端进程之间通信，而这就是刚才我们看到的静态网站实现的更下一层。

浏览器和服务器软件，把他们剥离到这一层，本质上就是两个依靠 Socket 通信的进程。只是我们这个 demo 里，他们传输的是从命令行输入的文字，而刚才那个静态网站，传输的是文本。

对于 web 技术栈来讲，目前理解到传输层 TCP/IP 已经足够。不需要知道 Socket 是怎么实现的，只要能够用 Socket 就已经很好了。

看到这里读者可能会有一点疑问，这怎么还越讲越底层了，按理说我就搭建一个网站，需要懂什么 Socket 和进程间通信呢，不是起一个服务器，然后用浏览器访问就好了嘛，HTTP已经帮我们打理好了一切。

其实我讲这个的目的就是为了讲清楚**计算机网络通信本质上就是进程之间通信**的原理。为之后的内容做铺垫。在现代 web 应用开发的过程中，你始终要有一个进程模型的概念在脑海之后，否则就是两眼一抹黑，学什么都是一片浆糊。

项目代码：

[github/tcp_udp_test](https://github.com/quaeast/tcp_udp_test)

## 农业革命：动态网站和模板语言


## 文明之光：AJAX 与 RESTful API


## 后现代社会：nodejs
