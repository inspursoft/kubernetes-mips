# kubernetes-mips
Kubernetes running on MIPS CPU architecture, knowledge sharing and technical support.

# 简介：
MIPS芯片架构用的是精简指令系统计算结构（RISC结构），是国产化安全可靠平台的主力架构之一。 如何在MIPS芯片架构上搭建容器云平台，尤其是Kubernetes平台是非常有意义和挑战的工作。 本项目的目的是为广大MIPS用户提供Kubernetes on MIPS的技术共享和支持。

# Reference:
[Kubernetes issue #85932 kubernetes e2e tests images for arch mips64el](https://github.com/kubernetes/kubernetes/issues/85932)

[Kubernetes issue #34600 Build kubernetes for a new arch---mips6el](https://github.com/kubernetes/kubernetes/issues/34600)

# k8s-conformance
1. 一致性测试所需镜像[列表](k8s-conformace-images)，在国内需要将`gcr.io`替换为`gcr.azk8s.cn`、`quay.io`替换为`quay.azk8s.cn`、`k8s.gcr.io`替换为`gcr.azk8s.cn`，建议提前将镜像在集群各个节点下载好
2. 在master节点根据cncf[官方文档](https://github.com/cncf/k8s-conformance/blob/master/instructions.md)安装sonobuoy并进行一致性测试
