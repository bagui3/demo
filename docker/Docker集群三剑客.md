Docker集群管理三剑客各自的只能和相互集成完成什么工作？  
Docker集群管理三剑客：  
Docker machine  
Docker compose  
Docker swarm   
问题：  
1、三个东西各自的职能是什么？  
2、三个东西相互之间集成完成什么工作？  
ps：集成好像只有  
（1）Docker machine 和Docker swarm 集成，  
（2）Docker compose 和Docker swarm 集成，  
这两个集成，没有Docker machine 和Docker compose的集成。

Machine是在虚拟机上运行docker，通过machine可以快速在虚拟机里面部署docker，因此如果是非linux环境，实际是启动一个虚拟机，然后远程上去的，适合学习和测试。  
Compose是docker自带的编排工具，最初处理多个容器在一台主机上的启动和依赖。  
Swarm是自带的集群管理工具，通过它可以把多个docker虚拟成一个集群，同时支持原生API，正因为如此compose结合swarm后就可以跨主机编排。  
不过swarm还是比较新的集群管理工具，稳定性还有待提高。
