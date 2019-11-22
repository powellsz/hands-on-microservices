# 集装箱、容器化、容器编排

## 集装箱革命、容器化革命

前面已经提到，微服务架构离不开容器技术。为什么需要容器呢？

我们先来看一个海运的例子。

* 传统海运：尽管货海运已经出现了几千年，但直到20世纪中叶，货物运输依然是一种劳动力密集型工作。码头雇佣了数以万计的工人，将货物从岸上搬运到船舱中。由于货物的种类繁多，体积不一、传送带、铲车都不能根本的解决问题，货物装卸依然大量依赖人工，而且装卸时间大量占用了港口时间，装卸价格居高不下。
* 集装箱革命：20世纪50年代开始，集装箱逐渐走向商用的舞台。货物在岸上按照整齐的规格码放整齐，从而可以封装进集装箱。而装卸货物只需要机械来搬运集装箱即可，极大提高了港口的装卸效率。

集装箱革命使得货物的装卸成本从5美元/吨骤降到16美分/吨，节约了97%...

容器技术的兴起，也成为了运维领域的另一场"集装箱式革命"：

- 容器就是集装箱
- 货物则是运行与容器中的、各式应用程序。

容器为运维工作带来了如下革命性进展：

- 容器的标准化：为了让应用程序在生产机上跑起来，经常需要做各种不同操作系统的安装，依赖软件库的安装、环境配置......这些过程非常繁琐，还经常会由于版本的细微差异，和开发环境不一致，出现“这个程序本地好好的，放到服务器上就崩溃”这类情况。容器可以使用统一的描述语言，快速构建出完全相同的、标准化环境，从而解决运行环境的问题。
- 容器的隔离化：此外，不同的应用程序需要不同的应用环境，如果都部署在一台物理机上，很可能会发生包、依赖冲突，导致无法运维，而容器可以为运行在同一台物理机上的应用程序，创建不同的隔离环境。

不仅在运维领域，容器技术在开发环境的搭建、软件教学等领域，也产生了深远的影响。如果你使用过Docker，相信一定对容器带来的变革深有感触，这里就不再一一列举:-)

## 容器、容器编排

如果你应用过容器技术，那么一定听说过该领域内最迟手可热的两个技术：Docker和Kubernetes。

同样都是容器化技术的代表，这两者有什么不同呢？

我们来看一下基本定义：

- Docker：一种容器化引擎
- Kubernetes：一种容器服务的编排系统

Docker的定义比较好理解，它是一种容器的运行时环境。此外，Docker还提供了Dockerfile，这是一种运行环境描述语言。我们可以借助它来快速构建出应用程序所需的、可移植的环境。

Kubernetes的“容器编排”定位，就不是很好理解了，我们先来看一些应用容器技术时遇到的实际问题：

- 如何部署一个应用的多个结点，并进行自动的负载均衡？
- 应用不是孤立的，容器的运行也会有依赖关系，如何进行管理？
- 如何在不影响业务运行的前提下，升级容器（内的应用）？
- 如何在容器应用挂掉的时候，自动恢复故障？

上述问题，已经超越了容器引擎的管理范畴，这些就是“容器编排”系统所要考虑的事情了。

从上述例子我们不难看出，将Docker直接与Kubernetes来进行比较，并不科学，因为他们不是同一个范畴的技术。

实际上，容器引擎有很多种，除了最流行的Docker外，还有[rkt](https://coreos.com/rkt/docs/latest/)、[LXC](https://linuxcontainers.org/)等。从容器编排引擎的角度来看，无论是Docker、rkt还是LXC，都只是运行时引擎，都是可以相互替换的。

类似地，容器编排引擎也有很多种，除了最流行的Kubernetes外，还有[Swarm](https://docs.docker.com/engine/swarm/)、[MESOS](http://mesos.apache.org/)。只不过后两者的发展并不顺利，Kubernetes已经获得了容器编排领域的霸主地位。

前面谈了Docker与Kubernetes的许多不同，但他们也有一些共同点：

- 都是基于容器技术
- 都是采用GO语言编写的
- 都是用yaml作为配置文件格式
- 都是开源社区项目

以Docker为代表的容器技术、以Kubernetes为代表的容器编排技术，也对微服务的发展也起到了推动作用。

试想一下如果你将一个单体服务拆分为10个微服务，部署、运维成本将陡然上升。如何解决这些问题呢？这恰好是容器、容器编排的用武之地。

从容器一下子跳到微服务，你可能还看的有些懵，不要紧，我会在本章接下来的章节为你逐步展开。

## 思考与拓展

1. 如果你想了解更多关于容器、容器编排的事情，可以参考容器周刊上的一篇文章[《Kubernetes vs. Docker: A Primer》](https://containerjournal.com/topics/container-ecosystems/kubernetes-vs-docker-a-primer/)
2. 不同的容器引擎Docker、rkt等，各有什么优劣么？
3. Swarm与Docker出自同一公司。为什么Docker引擎成功了，Swarm编排引擎却被Kubernetes打败了呢？






