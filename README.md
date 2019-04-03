# NEO-CLI-NEL:
[English](#en) [简体中文](#zh)

<a name="zh"></a>

# 概述:

NEL团队在开发项目的过程中会遇到一些特定的需求，NEO-CLI并不能直接满足。因此修改了NEO-CLI的部分代码，加入了一些定制的功能，推出了NEL的定制版节点NEO-CLI-NEL。NEL定制版的节点包含了原NEO节点的所有功能。并保证安全性和原NEO节点一样。
注：这些需求包含但不仅限于`数据直接录入Mongodb`，`合约操作过程的记录`，`通过leveldb操作来快速恢复数据`。

# 环境要求和如何使用:

NEO-CLI-NEL的环境要求以及使用方法和原NEO-CLI一样，这里就不重复介绍。可以查阅https://github.com/neo-project/neo-cli

# 定制版功能介绍：
## 基于leveldb操作记录的快速同步
###
