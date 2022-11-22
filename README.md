# rpcSample
The git repo for the RPC transmission sample
2022.11.22


## 简介
rpcSample为本增强现实应用开发引擎微服务/rpc的仓库。提供测试样例。


## 工程管理

### 第三方库

本项目已在以下版本上测试：
- Windows操作系统
- Clion (MSVC编译器)
- Boost 1.80.0(使用MSVC编译器进行编译)
- OpenCV 4.6.0 (使用MSVC编译器进行编译)

### 工程构建
(1) 使用CMake进行工程的构建<br>
(2) 需要在rpc_client中修改对应的数据目录（path）<br>
(3) 根据自己库目录在CmakeList.txt中修改Opencv等库的位置<br>
(4) 先运行rpc_server，再运行rpc_client样例进行测试<br>

## 数据

使用之江实验室提供的卫星数据进行重建，链接: https://pan.baidu.com/s/1BAVPtgFZ09T5UUxWYaXbLg  密码: c8ea

