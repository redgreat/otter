<h1>clone自阿里云开源仓</h1>
<strong>修改内容：</strong>
<ol>
<li>更换mysql驱动为8.0.30</li>
<li>升级 druid版本为1.2.6(因最新版canal依赖已升级,原始提供版本已不满足)</li>
<li>升级fastjson版本为1.2.79</li>
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