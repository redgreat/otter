<h1>clone自阿里云开源仓</h1>
<strong>修改内容：</strong>
<ol>
<li>更换mysql驱动为8.0.30</li>
<li>升级 druid版本为1.2.6(因最新版canal依赖已升级,原始提供版本已不满足)</li>
<li>升级fastjson版本为1.2.79</li>
<li>2022-11-21 升级fastjson版本为1.2.83</li>
<li>2022-12-26 升级dubbo版本为2.6.12</li>
</ol>
<strong>环境搭建：</strong>
<ol>
<li>更换maven仓地址为阿里云</li>
<li>进入 $otter_home/lib 目录</li>
<li>执行：bash install.sh</li>
</ol>
<strong>打包：</strong>
<ol>
<li>进入$otter_home目录</li>
<li>执行：mvn clean install -Dmaven.test.skip -Denv=release</li>
<li>发布包位置：$otter_home/target</li>
</ol>
<strong>线上升级：</strong>
<ol>
<li>利用node高可用，首先搭建node2节点，配置文件中设置nodeid为2；</li>
<li>打开manager，添加node节点2；</li>
<li>停用需要迁移的channel，编辑channel下的pipline，并将node2节点添加至可用；</li>
<li>全部编辑完毕后，启动两node节点，观察其运行正常性；</li>
<li>暂停所有channel节点，关闭node1，开启node2，恢复所有channel节点状态，在manager端观察其运行正常性；</li>
<li>搭建manager2节点，因端口与manager1有冲突，这里切记，一定不能同时开启两节点；</li>
<li>关闭manager1节点，打开manager2节点，观察所有channel运行正常性；</li>
<li>校验/查看数据同步正常性， 切换成功。</li>
</ol>