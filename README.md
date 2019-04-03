# NEO-CLI-NEL:
[English](#en) [简体中文](#zh)

<a name="zh"></a>

## 概述:

NEL团队在开发项目的过程中会遇到一些特定的需求，NEO-CLI并不能直接满足。因此修改了NEO-CLI的部分代码，加入了一些定制的功能，推出了NEL的定制版节点NEO-CLI-NEL。NEL定制版的节点包含了原NEO节点的所有功能。并保证安全性和原NEO节点一样。
注：这些需求包含但不仅限于`数据直接录入Mongodb`，`合约操作过程的记录`，`通过leveldb操作来快速恢复数据`。

## 环境要求和如何使用:

NEO-CLI-NEL的环境要求以及使用方法和原NEO-CLI一样，这里就不重复介绍。可以查阅https://github.com/neo-project/neo-cli
如果需要使用NEL特有的一些功能，可以参阅下面的定制版功能介绍。

## 定制版功能介绍：
### 基于leveldb操作记录的快速同步
#### 简介：
去除节点在初次同步时对数据的验证分类，直接通过leveldb操作来快速同步数据。
这个功能以插件的形式实现。
具体可以查阅https://github.com/NewEconoLab/Plugins 工程中的RestoreDB项目。
#### 注意项：
与原版的插件不一样，RestoreDB这个插件需要放在NEL_Plugins目录下。
#### 使用流程：
 -克隆本仓库；
 -发布这个工程；
 -创建NEL_Plugins文件夹（路径类似于/neo-cli/bin/debug/netcoreapp2.1/NEL_Plugins）
 -克隆Plugins仓库（https://github.com/NewEconoLab/Plugins ）
 -发布RestoreDB工程
 -将发布RestoreDB工程生成的.dll文件以及包含配置文件的文件夹复制到NEL_Plugins文件夹中（此时NEL_Plugins文件夹中应该有Restore.dll以及一个包含config.json文件的Restore文件夹）
 -回到neo-cli.dll所在目录，下载同步数据包 
  -testnet： http://nel-acc.oss-cn-hangzhou.aliyuncs.com/release.0-2400000.zip
  -mainnet: 暂无
 -使用dotnet neo.cli 命令启动节点，如果出现"正在导入0-1000000高度数据"则意味着正在快速恢复数据。
	-如果需要额外的启动项，例如--rpc --log等，使用方法和原版节点一样。
