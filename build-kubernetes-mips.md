## 说明

本文档介绍mips架构下，构建kubernetes v1.15.3版本的可执行文件步骤。 构建基础环境如下。 

软件                  | 版本
----------------------|--------------------------
操作系统               | NeoKylin Linux Server 7.0
docker-ce             | v18.09.8-ce
git                   | 1.8.3 +


## Step 1: 下载kubernetes-mips项目源码。

   ```sh
      $ git clone https://github.com/inspursoft/kubernetes-mips.git
   ```

## Step 2: 在kubernetes-mips项目源码同级目录下，下载kubernetes源码并切换到v1.15.3版本.

   ```sh
      $ git clone https://github.com/kubernetes/kubernetes.git
      $ cd kubernetes  && git checkout v1.15.3
      $ cp ../kubernetes-mips/0001-build-mips-k8s.patch  .
   ```

## Step 3: 在kubernetes项目主目录，拷贝kubernetes-mips项目中补丁0001-build-mips-k8s.patch到当前目录并打补丁。

   ```sh
      $ cp ../kubernetes-mips/0001-build-mips-k8s.patch  .
      $ git apply 0001-build-mips-k8s.patch
   ```

## Step 4: 下载golang镜像用于编译kubernetes源码

   ```sh
      $ docker pull inspursoft/golang-mips:1.12.9
   ```

## Step 5: 启动docker容器编译kubernetes源码

   ```sh
      $ docker run -it --rm -v `pwd`/kubernetes:/go/src/k8s.io/kubernetes --workdir /go/src/k8s.io/kubernetes  inspursoft/golang-mips:1.12.9 bash -c  "yum install -y make which && make"
   ```

构建成功后，kubernetes的可执行文件放在项目主目录的_output/local/go/bin文件夹下。
