# Large-Scale-SDN-Testbeds-ZH

## A Survey on Large-Scale Software Defined Networking (SDN) Testbeds: Approaches and Challenges

## Structure:

**I.Introduction**

**II.Related Works**

**III.Background Knowledge**

- A.Brief Introduction of SDN
- B.Brief Introduction of Traditional Network Experiment Methods

**IV.Overview of SDN Testbeds**

- A.Advantages of SDN Testbeds Over Traditional Network Experiment Methods
- B.Design Issues of Large-Scale SDN Testbeds
- C.Key Technologies of Large-Scale SDN Testbeds

**V.Different Large-Scale SDN Testbeds Implementations**

- A.GENI OpenFlow
- B.OFELIA
- C.RISE
- D.OF@TEIN
- E.OpenLab

**VI.Comparison of SDN Testbeds**

- A.Design Objectives	
- B.Key Technologies
- C.Network Deployment
- D.Experiments

**VII.Challenges and Future Works**

- A.Federation
- B.Slicing
- C.Compatibility with Existing Network Equipment

**VIII.Conclusion**

### Abstract

本文是对SDN测试平台的综述，介绍了SDN测试平台的北京以及相关知识，接着介绍了SDN测试平台的Overview。此外介绍了五种典型的大规模SDN测试平台，并将它们进行了深度的对比。最后，介绍了SDN测试平台的挑战及未来工作。

### I.Introduction

传统网络面临挑战，SDN的出现为解决传统网络的问题带来了新的转机。为验证网络设计和算法的性能，实现了大规模的SDN测试平台。研究人员设想这些实验平台将是下一代互联网络的温床。大部分的测试平台是基于OpenFlow的，这些平台有美国的GENI，欧洲的OFELIA、OpenLab，日本的RISE以及南朝鲜的OF@TEIN。这些SDN测试平台为未来网络研究做出了积极的贡献。

本文对大规模的SDN测试平台进行了详细的说明，展示了设计目标、关键技术、网络部署以及实验，此外，我们对大规模SDN测试平台面临的挑战进行了探讨。

### II.Related Works

介绍了现有SDN领域的综述论文。包括：

- SDN components
- SDN architechture
- SDN/OpenFlow implementations
- SDN controllers
- SDON(Software-Defined Optical Network)
- SDWN
- SDN hypervisors
- NV in Data Center
- NV methods
- Virtualization approaches in wireless network

### III.Background Knowledge

#### A.Brief Introduction of SDN

#### B.Brief Introduction of Traditional Network Experiment Methods

研究人员使用模拟器、仿真器以及网络测试平台对新型网络设计和算法进行验证。模拟器(eg.NS2/NS3)基于网络拓扑和特征建立对应的模拟环境。仿真平台(eg.Emulab)使用虚拟化服务器集群基于软件来模拟分布式网络和真实的流量。

**网络测试平台能够为研究人员提供真实的流量和真实的网络设备**。有很多大规模的测试平台：APE致力于为ad-hoc路由协议提供真实的评估环境；Planetlab是一个用于广泛服务研究(broad-coverage services)的overlay测试平台；UltraScienceNet被设计为开发新的网络技术，服务于下一代大规模科技应用；StarBED专注于运行用于软硬件实现的实际程序代码；LISP-LAB专注于LISP(Locator/ID Seperation Protocol)应用和开源LISP的实现；GENI是一个分布式的实验环境，用于大规模的网络实验；GpENI是一个可编程的网络测试平台，为研究人员提供了对网络协议栈的编程能力。

这些平台通常基于不同类型的隧道技术，用于将这些网络在Internet上互联。有一些传统的隧道技术在基于SDN的环境中依然十分有用：VLAN、Q-in-Q、MPLS、GRE、VxLAN、NVGRE(Network Virtualization using GRE)。

相比于模拟器，网络测试平台对于网络实验来说更加方便，因为**使用了真实的网络流量**；相比于仿真平台，网络测试平台**使硬件网络设备参与了进来，并且能够在产品网络上运行，提供高性能和可拓展性**。但是这些平台中，传统的网络设备的控制过于封闭，这降低了实验的灵活性和自动化。

[table2]

### Overview of SDN Testbeds

#### A.Advantages of SDN Testbeds Over Traditional Network Experiment Methods

SDN改变了传统网络的模式和运行机制，在网络测试平台中应用SDN的方法，特别是OpenFlow，能够完美解决不灵活和不高效的自动化问题：

- **Easier Setup**
- **Optimal Control**
- **Enhanced Network Virtualization:** SDN中的hypervisor能够自动简化复杂和有错误倾向(error-prone)的操作。

至今，大规模的SDN测试平台已经在许多国家应用，并促进了创新的发展。

#### B.Design Issues of Large-Scale SDN Testbeds

大规模的SDN测试平台设计包括几个理论上和实际上的方面，在设计这些平台的时候，需要谨慎考虑这些问题。

**1.Automation**：使用传统的方法，在真实的主机和网络设备之间运行实验需要许多复杂的人为配置，并且一定程度上导致了过去几十年网络创新的缓慢。SDN为网络自动化部署提供了可编程性，一些计算机虚拟化技术能够为VM的调度和供应提供接口，SDN测试平台应该结合这两种技术来提供完全自动化的网络创新环境。

**2.Flexibility**：变化的可控制性有时候对于网络研究来说是非常重要的。SDN测试平台需要提供灵活性，以支持研究人员修改网络设备的数目或者调整链路带宽。

**3.Scalability**：可拓展性依然是一个问题，特别是当大规模SDN测试平台的范围是国家级别的或者是洲际的。如何将地理上的分布或者是异构的网络域，通过统一的管理和控制连接起来是需要谨慎考虑的。

**4.Security**：在所有的IT基础架构中，安全是永恒的主题。对于SDN测试平台来说，当不同的网络实验在同一片架构上执行时需要保证安全性，包括认证的管理安全、授权以及计费(AAA)机制以及基于切片技术的流量隔离。

考虑到这些因素，SDN测试平台需要被认可为“cloud especially for network researcher”，提供计算和网络资源(如果需要的话，也要整合存储资源)来服务网络研究租户，也常被称为切片。

##### C.Key Technologies of Large-Scale SDN Testbeds

**对于一个大规模的SDN测试平台而言，需要实现三个主要的技术，包括管理、网络以及切片，这些技术对于构建和运行SDN测试平台的关键技术**。

- Management Technologies：首先需要指出的是，这里的管理技术区别于只关心network的SDN管理技术(eg.OF-CONFIG和OVSDB)，SDN测试平台中的管理技术从不同的角度看问题，关注VM、network以及实验的运行状态。**管理技术的整体实现通常称为控制框架**。

  用户向与其协作的Web界面提交他们的资源应用，描述了他们实验的网络拓扑。Underlaying的资源，如VM和网络设备应该能够根据这些应用提供可调度性。VM控制依赖于服务器虚拟化技术，网络设备的控制依赖于切片技术，而**管理技术只是调用API来执行实验应用。一旦实验被触发，其状态应该能够被收集和分析。当实验结束时，相关的资源应该被释放**。

  换句话说，**实验的整个流程都应该能够支持管理技术**。此外，应该支持用于安全的AAA机制以及用于内部测试平台拓展性的统一机制(federated mechanisms for inter-testbeds scalability)。

- Networking Technologies：**数据平面的网络设计SDN交换机的互联，包括物理和逻辑交换机**。在纯SDN领域，交换机应该能够直接使用铜线和光纤连接，有时候，数据平面是覆盖于在传统网络之上的。

  **管理/控制平面网络设计管理/控制单元之间如何互联**。管理单元包括实现管理技术的软件，控制单元包括切片工具或者是实验SDN控制器。管理/控制平面网络主要关心接入(access)，所以只要是三层的连接性就足够了。

- Slicing Technologies：为了隔离实验流量，切片技术是必须实现的。基于SDN的虚拟化通常作为一个应用，整合于通用的SDN控制平台，该方法广泛使用于数据中心虚拟化：应用管理所有的网络转发逻辑来连接或者隔离流量，数据中心用户无需关心网络是如何转发数据报的。但是在SDN测试平台方面是完全不一样的，**因为SDN测试平台的用户可能需要对他们实验的转发进行控制，以执行二到四层的创新**，而不是在网络的顶层运行七层的应用，此外他们还**需要使用他们自己的控制器**。所以在SDN测试平台中，**切片技术应该能够协调不同租户的控制器，来对用户数据平面的流量做隔离，使用户的控制器无感知其他用户的网络和控制器**。

  为实现这些目标，在**SDN测试平台中切片技术的实现需要在SDN控制平台之下实现**，它们通常基于OpenFlow协议，并处于SDN控制器和交换机之间，作为一个OpenFlow的代理，将OpenFlow的消息进行修改，以对数据平面流量，使每个用户的控制器都感觉像拥有自己的测试网络一般。

  **SDN测试平台中的切片工具通常被称为网络的hypervisor**。

### V.Different Large-Scale SDN Testbeds Implementations

该部分会对五个典型的大规模SDN测试平台从以下四个方面进行介绍：(1)Design Objectives and Development：测试平台的Overview；(2)Key Technologies：管理、网络以及切片技术的介绍；(3)Network Deployment：测试平台的实现；(4)Experiment：介绍了已执行的SDN实验。

#### A.GENI OpenFlow

**1.Design Objectives and Development**：

GENI(Global Environment for Network Innovation)是美国的NSF支持的，并使用创新的网络技术比如网络虚拟化、OpenFlow和SDN，来保证网络创新和规模性的实验实体。GENI使用螺旋式的演变发展模型，在头两个阶段，创建了一个端到端的工作原型，并朝向可持续的实验发展；在第三个阶段，GENI使用了OpenFlow技术，并将OpenFlow交换机部署至校园网；现如今GENI是处于第六个阶段，这个阶段的主要目标包括：(1)通过更好的工具和服务吸引更多的实验；(2)通过部署GENI的框架以及增加支持GENI的园区网增大GENI的规模；(3)修正GENI的指令及测量系统。

**OpenFlow逐渐成为GENI中的支撑技术，它保证了GENI为租户提供真实的环境以进行规模实验，同时也实现了GENI的核心概念，切片和深度可编程性**。在GENI中，OpenFlow交换机提供深度的可编程性，给予了网络管理人员确切定义策略的能力，用以管理网络安全。GENI OpenFlow现在对大家开放，用户能够通过GENI portal接触它。

**2.Key Technologies**：

GENI的关键技术主要包括三个方面：控制框架、网络技术以及切片技术。

> a)管理技术：

为了建立一个大规模且合乎逻辑的架构，GENI使用了一个联合的架构，也就是说，**GENI从不同的供应商处获取资源。每一个供应商管理它的资源并且为实验人员提供使用资源的权力**。GENI控制框架GCF由四个部分组成：GENI元操作中心(GMOC)，交换中心(Clearinghouse)，工具以及资源池(Aggregates)，它们之间的关系如图所示：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig4.png)

- GENI工具：主要用于管理和控制GENI资源。
- GENI资源池：为实验人员提供资源。
- GMOC：发现、报告以及升级GENI架构，以保证GENI架构的健康；将实验与GENI操作员们相连接。
- GENI交换中心：将实验人员、GENI资源池以及GMOC联系起来，为GENI提供必需的信任度、认证、责任以及授权服务。

以上四个部分是通过一种编排方式联系起来的。

**GENI实验的生命周期主要由这三个阶段组成：设计/设置，执行以及结束**。

- **设计/设置阶段**：(1)用户设置一个GENI账号，并加入GENI项目，这一步中，GENI将拥有本地策略的虚拟机服务聚集起来，这些服务决定了它们信任和接受的、负责同意用户、项目以及切片以及发布不同证件的协调人；(2)用户请求交换中心以获取资源管理者的列表；(3)用户请求资源管理者，资源管理者返回完善的远距离访问接口，用于创建切片和保留资源。
- **执行阶段**：用户登录通过GENI工具至节点以执行他们的实验，并监控实验的执行。
- **结束阶段**：用户应该删除资源并结束他们的实验。

上述完整的生命周期是由GMOC保证的。

> b)网络技术：

GENI基于实验需求、现有网络以及潜在的新连接提供了许多网络技术的选项。图5是一个内部互联园区网的案例，展示了一个简单且典型的网络连接拓扑：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig5.png)

**GENI OpenFlow测试平台是由控制和管理平面以及数据平面组成的**。 **控制和管理平面用于配置和管理在数据平面执行的实验**，用户可以通过在Internet和上层隧道技术上的SSH连接来访问切片。控制路径通常是跑管理流量，比如控制和监控的数据。**数据平面包含用户的切片并负责执行实验**，它支持使用三层和二层的技术，二层的选项通常用于连接园区级、区域级和国家级的研究网络，三层的选项通常是上层的隧道，将控制平面和数据平面相连接，并被实验人员用于管理它们的切片。二层的技术包括Single VLAN、VLAN Translation、L2 Tunneling、Fiber Connection。

> c)切片技术

GENI采用了PlanetLab测试平台的切片技术，切片能力是支持虚拟化技术的能力，用于支持不同实验的并行以提升网络资源的利用率。传统的网络使用VLAN来实现基本的虚拟化策略，但是在GENI为了提供更灵活的网络虚拟化方法，使用了支持OpenFlow的组件来允许多租户控制器管理同一片资源。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig6.png)

主要有三种虚拟化技术：FlowVisor、OVX、Flowspace Firewall。

FlowVisor：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig7.png)

OpenVirteX：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig8.png)

FlowSpace Firewall(FSFW)：

FSFW是印第安纳大学开发的一个用于提供网络功能虚拟化的Floodlight插件，相比于其他切片工具，**FSFW更加关心不同控制器之间的一致性：如果一个控制器发送了一个能够导致数据平面矛盾的规则，FSFW拒绝该规则并返回错误信息**。由于该功能，FSFW能够处于物理OpenFlow交换机和其他切片工具之间。

**3.Network Deployment**：

主要是从两个方面介绍GENI网络部署，园区网络以及国家级别的骨干网络。

> a)园区网络部署

Stanford University Deployment：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig9.png)

> b)国家级骨干网络部署

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig10.png)

**4.Experiments**：

包括两个主要的实验。第一个实验设计了一个系统用以提供GENI的研究人员使用无线资源的能力；第二个实验介绍了SDN Open Transport Switch(OTS)的原型，该系统拓展OpenFlow以支持可选的传输能力，来保证应用驱动可选的传输带宽服务。

实验一：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig11.png)

实验二：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig12.png)

#### B.OFELIA

**1.Design Objectives and Development**：

OFELIA在2010年的秋天由欧洲 Seventh Framework Programme (FP7) 项目启动，**它的主要目标是设置一个多层、多域以及地理上分布的未来网络测试平台实体，能够适应不同类型的流量，以及为日常使用和基于OpenFlow的新型网络实验提供服务**。为了实现这些目标，OFELIA的设计遵守这些信条：

- Flexibility and modularity：预先定义的功能应该是受限的，模块的发展应该具备拓展性；
- Fidelity use and easy use：能够适应产品流量，OAM(操作维护管理)应该尽可能简化；
- Resource isolation and security：需要实现虚拟化以隔离不同流量，需要保证AAA；
- Island autonomy and federation：不同的领域(island)管理应该在行政上是分离的，并且应该支持领域间的联合。

OFELIA的第一个时期(duration)是由三个阶段组成的。第一个阶段OFELIA成功设置了underlaying的实体，包括一些OpenFlow的交换机和VM实体；第二个阶段，OFELIA实现了不同域之间的内部连接，并往无线和光纤领域拓展了SDN实验；第三个阶段加入了OFELIA控制框架为Internet的其他实体和测试平台提供连接。**OFELIA已经不再提供接入服务了，它只接收EU-limited的开放调用**。

**2.Key Technologies：**

> a)管理技术

**OFELIA开发了OFELIA控制框架OCF作为编排器，用来保证操作者对于underlaying的实体的管理以及用户对于它们实验的接入**。OCF主要致力于对资源分配进行仲裁，自动化测试平台的管理，简化实验的生命周期。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig13.png)

**在该架构中定义了三个层次，入口(portal)、互联中心(Clearinghouse)以及资源管理**。入口用于解决用户对他们切片的操作并简化操作员的管理；互联中心用于在域间同步用户的账户和权力，并通过 Lightweight Directory Access Protocol (LDAP) 服务器提供通用的认证；资源管理的模块分别是虚拟化聚合模块(AM)和OpenFlow聚合模块，AM将资源管理的接口与交换机中心相绑定，负责将VM聚合为切片，OpenFlow聚合模块，应用于网络切片规则和配置的管理。除了这些模块，还有其他有用的插件，这里不列举了。

**OCF的最初设计方法是从GENI中的用户案例和经验衍生出来的**。 

**OFELIA实验的周期主要由三个阶段组成：配置、执行以及结束**。

- 配置阶段：分为三步；首先，初始化时，用户通过基于web的用户接口配置他们的实验，这是由OCF的Portal模块提供的；第二步，用户请求互联中心以获取权限；最后，用户请求资源管理者以获取用于创建切片的资源。
- 执行阶段：用户可以登陆并进行实验。
- 结束阶段：用户删除并释放资源。

> b)网络技术

除了实验网，OFELIA有两个带外(out-of-band)网络用于控制和管理，所有的OFELIA域与现在都与OFELIA hub内部进行互联，形成了一个星型网络。OFELIA hub作为一个中转站来在域间传递实验以及控制流量。

- 实验网络：涵盖所有的OFELIA域。
- 控制和管理网络：带外的网络，与不同的OFELIA域互联。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig14.png)

> c)切片技术

FlowVisor能够用于切片OFELIA，但是它有很多缺陷，于是有些研究人员基于FlowVisor研究出了VeRTIGO、Optical FlowVisor来解决这些问题。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig15.png)

> d)硬件层抽象

随着SDN被广泛接受，新的网络设备将它们的FE和CE相分离。同时使用OpenFlow设备和非OpenFlow设备的想法推动了硬件抽象层(HAL)的发展。HAL诞生于Alien项目，一个想要**将非OpenFlow的平台整合至OFELIA的基于OpenFlow的架构中，并统一控制和管理异构的网络设备**。HAL屏蔽了不同的技术和厂商特定的细节，有两个分离的层次，硬件接口层(HIL)和硬件表示层(HPL)。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig16.png)

- HIL：**HIL的组件协同工作，作为一个通用的控制和管理协议，比如OpenFlow或者其他的SDN南向，并且向上屏蔽了底层硬件平台的复杂性**。HIL组件在控制器和转发设备之间起到一个代理的作用，包括以下两个子组件：虚拟化组件用于向支持HAL的设备提供虚拟化能力；OpenFlow的endpoint是OpenFlow通道的端点，维持与上层控制器的通信，并向下发送类OpenFlow的流表。
- HPL：HPL组件区别于不同的设备类型。一般来说，北向的HPL API接收到来自HIL的流表以控制转发。**设备信息模型代表了OpenFlow交换机的状态，且独立于底层的平台硬件。设备驱动通过物理硬件实现了数据转发，它是平台相关的，将所有OpenFlow的流表转换为特定的语言，并模拟OpenFlow交换机的转发行为**。

**3.Network Deployment**：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig17.png)

**4.Experiments**：

在OFELIA上实现了许多优秀的实验，如光设备的整合以及在SDN中支持ICN。这一部分的具体细节请参照原文。

> a)光设备的整合

[table3]

OpenFlow-GMPLS：OF控制器与传统光设备相整合的架构。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig18.png)

> b)支持ICN

拓展OpenFlow协议，支持内容命名转发。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig19.png)

#### C.RISE

**1.Design Objectives and Development**：

Japan NICT在2009年，于JGN-X的基础上搭建了用于大规模网络实验的基础设施RISE。**RISE是一个SDN的测试平台，目的是为网络研究人员提供一个多租户和大规模的SDN实验测试环境**。RISE至今向外开放，已认证的用户能够根据他们的需求以获取RISE的资源。至今RISE已有三个版本。

> a)RISE 1.0

- 独立用户占用整个OpenFlow网络；
- Q-in-Q用于在OpenFlow交换机间转递用户数据报；
- 不提供虚拟机

> b)RISE 2.0

- 多租户共享物理基础设施；
- 虚拟有线技术取代了Q-in-Q，用于站点间内部连接；
- 向用户提供虚拟机

> c)RISE 3.0

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig20.png)

**2.Key Technologies**：

为省钱，RISE是建立在JGN-X的基础上的，物理路径层是由JGN-X现有的交换机组成的；RISE的网络技术只是添加了将JGN-X服务间专线进行共享的技术；拓扑虚拟化层专注于将RISE网络进行切片；RISE的编排器负责管理RISE的underlaying资源和实验。

> a)Management technologies：

**RISE希望根据用户的要求提供定制化的SDN实验，并需要自动化的操作来部署这些实验**。RISE编排器在RISE 3.0时开发，它帮助了RISE的管理人员们管理网络以及用户的实验。

在RISE中，面向用户的前端通信是提供web游览器的，使用北向API接收实验配置并展现实验状态。项目管理人员管理所有的underlaying资源和上层的实验，并驱动相关的管理模块提供虚拟服务器和交换机。RISE编排器通过发送和接收探查报文获取全局的物理拓扑信息和用户预配置的实验网络信息，这些信息用于管理物理OpenFlow交换机的流表项。用户可以很方便的使用RISE编排器来定制化实验，配置切片的时间少于10分钟。

RISE实验的周期由三个部分组成：设置、执行和结束。

- 设置：用户通过前端配置实验，项目管理者驱动VM管理者和OFS管理者提供VM和实验网络；
- 执行：用户通过前端登录节点，跑实验；
- 结束：用户删除并释放资源。

> b)Networking Technologies：

JGN-X是基于VLAN的网络测试平台，RISE刚刚开始时使用Q-in-Q来在JGN-X上跑overlay的网络，现在使用更加合适的EoMPLS技术取代了Q-in-Q。

- Q-in-Q
- EoMPLS

使用EoMPLS后，解决了原有MAC地址短缺的问题，且MPLS标签的长度远长于VLAN，使得RISE网络更有拓展性。

> c)Slicing Technologies：

RISE 1.0：一旦用户请求在RISE上运行实验，他就会占有所有的OpenFlow资源直到实验结束。

RISE 2.0：实现了虚拟交换机实例，最多能同时提供16个不同的切片。用户的VM需要通过特定的VLAN标签来与其他流量相隔离。

RISE 3.0：引入了拓扑虚拟化层，通过MAC地址重写实现了逻辑路径以弥补JGN-X的物理路径。但是仍然有排错等问题。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig21.png)

**3)Network Deployment**：

现在RISE已经在日本的十个站点部署了。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig22.png)

**4)Experiments**：

部署有视频流量实验(in Sapporo snow festival)和光场景。详见论文。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig23.png)

#### D.OF@TEIN

**1)Design Objectives and Development：**

OF@TEIN是韩国政府通过NIA(国家信息社会机构)捐赠的e-TEIN项目中的一个子项目，发布于2012年7月。**它的目的在于在TEIN4网络上逐渐建立和操作一个支持OpenFlow的SDN测试平台**。OF@GEIN是由韩国各大高校和国际的合作站点共同建立的，由GIST领导。

**OF@GEIN的设计专注于三个任务：设计SmartX Racks并做验证、站点部署并做内部连接、开发有用的SDN工具**。至今，OF@TEIN实现了这些目标，但是它不开放，事实上可以通过NREN 国家研究和教育网络访问。

**2)Key Technologies：**

> a)Management Technologies：

基于OFELIA控制架构，OF@TEIN开发了OF@TEIN接入口，它提供了实验的UI来创建切片和监控实验状态。通过接入口的接口，聚合了SmartX Rack和网络资源来服务于实验，记录流空间的资源以切片网络。特别地，OF@TEIN建立了SmartX自动中心来管理架构。

**OF@TEIN实验的周期由三个阶段组成：设置、执行和结束**：

- 设置：用户通过接入口设置实验，接入口提供实验UI以创建切片和观察实验状态；
- 执行：用户登录并执行实验；
- 结束：用户结束实验并释放资源。

> b)Network Technologies：

- 基于可感知OpenFlow的封装节点，并使用NVGRE隧道实现站点间互联。
- 设计SmartX Racks并部署与每一个OF@TEIN的站点，加速与TEIN NRENs内部的协作。
- OF@TEIN站点之间使用NVGRE隧道互联。
- OF@TEIN的控制和管理网络被设计为一种带外的overlay网。
- 除了OpenFlow，OVSDB也被OF@TEIN的管理者们使用。

> c)Slicing Technologies：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig24.png)

使用FlowVisor来切片网络，基于VLAN的切片架构。flowspace包括DPID和PortID。

**3)Network Deployment：**

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig25.png)

**4)Experiments：**

实现的实验包括OVSDB配置实验：使用OVSDB完成隧道部署，和自动化带宽测量实验。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig26.png)

#### E.OpenLab

**1)Design Objectives and Development：**

**OpenLab是一个FP7网络研究项目，致力于将现有的测试平台打造为开放、可拓展并可持续的网络架构，同时也为早期的、应用于未来网络研究的网络原型或者系统提供支持**。OpenLab始于2011年的九月，这个项目和一个多样化的应用和网络协议集在分支测试平台上部署于硬件和软件。SDN的方法，比如OpenFlow，已经引入该测试平台，现在它在无线和光领域都SDN化了。OpenLab现在通过OneLab接入口开放，不过有些节点不能使用。

**2)Key Technologies：**

> a)Management Technologies：

OpenLab中有一系列的可用的测试平台，大部分都使用它们自己的控制框架。在OpenLab中，SFA作为资源池的编排器，同时也进行了大量用于联合、开发其他框架的工作，比如Teagle和OMF。

**OpenLab实验的周期由三个阶段组成：设置、执行和结束**。

- 设置：用户通过接入口设置实验，接入口提供实验UI以创建切片和观察实验状态；
- 执行：用户登录并执行实验；
- 结束：用户结束实验并释放资源。

(注：和OF@TEIN章节中的阶段一样)

> b)Networking and Slicing Technologies：

OpenLab中的两个测试平台NITOS和PLE(PlanetLab Europe)主要采用了OpenFlow。这里对两个平台进行介绍。

**NITOS**

NITOS OpenFlow：

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig27.png)

- 控制网络控制SDN实验精确的执行，并负责监控underlaying的网络。
- 管理网络负责通过到机架管理网卡(Chassis Manager Card)的HTTP请求控制接入节点的状态。
- NITOS提供远程接入OpenFlow交换机的能力，通过FlowVisor切片底层网络。
- NITOS调度器在新的保留插槽初始化时配置FlowVisor，编排用户流量。

**PlanetLab Europe：**

PLE是PlanetLab的一部分，是通过sliver-ovs(ovs的改动版本)支持OpenFlow的。sliver-ovs能够在一个节点实例化一个或者多个OpenFlow交换机，称为slivers。在一个PLE切片中的slivers通过虚拟电缆进行通信，是通过Internet上的UDP隧道实现的。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig28.png)

**3)Experiments：**

EXPRESS项目是一个可迅速恢复的SDN系统，目的是为了拓展SDN域在间歇性连接网络环境下的工作能力。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig29.png)

Secure BGP routing 安全BGP路由，测试了一种应用于安全BGP路由的SDN方法：Secured Path State Protocol(PSP-SEC)路由协议。

![](https://github.com/Wasdns/Large-Scale-SDN-Testbeds-ZH/blob/master/figures/fig30.png)
