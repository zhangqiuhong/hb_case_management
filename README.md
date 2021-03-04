# hb_case_management [![Build Status](https://travis-ci.org/openatx/uiautomator2.svg?branch=master)](https://github.com/zhangqiuhong/hb_case_management)  ![PyPI](https://img.shields.io/pypi/pyversions/uiautomator2.svg) [![Windows Build](https://ci.appveyor.com/api/projects/status/github/openatx/uiautomator2)](https://ci.appveyor.com/project/openatx/uiautomator2)

<h5>依赖库信息</h5>

- [![Django](https://img.shields.io/pypi/v/uiautomator2.svg?label=django)](https://pypi.python.org/pypi/django)
- ![djangorestframework](https://img.shields.io/pypi/v/adbutils.svg?label=djangorestframework)
- ![PyPI](https://img.shields.io/pypi/v/adbutils.svg?label=PyMySQL)
- ![PyPI](https://img.shields.io/pypi/v/requests.svg?label=XMind)
- ![PyPI](https://img.shields.io/pypi/v/lxml.svg?label=opencv-python-headless)

**项目简介** 

<p align="left"><img src="docs/img/qqgroup.png" /></div>

[hb_case_management]以下简称TCM是一款面向软件测试相关从业者提供用例管理的工具，基于python的Django rest-framework、vue、nodejs等主流应用技术开发。
在部分UI方面参考了[飞蛾](https://feie.work/) 的设计风格并进行了小幅改动，增加了常用功能的便捷入口，去掉了繁复操作，降低了测试人员的使用成本，且完全开源免费，不限使用人数。

**产品优势** 

* 测试用例采用经典树形结构与脑图的双向管理模式，用户可根据自己喜好创建用例展现形式
* 脑图可多人在线同时创建、编辑
* 支持Excel/xmind文件进行导入或导出用例
* 可根据任务/需求维度组织部分用例形成测试计划 同时可向开发人员提供自测计划
* 集合了缺陷管理功能


## Requirements
- Django版本 3.0+
- Python 3.6+ (不支持2.7）
- Node.js 10+
- nginx 1.19.0+
- mysql 5.7+
- docker 2.3+



## QUICK START

> 本应用集成了dockerfile docker-compose, 同时也支持原始的服务器中直接部署的方式


# docker方式

1. 安装docker
    
    请参考官网：<https://www.docker.com/get-started>
    
    ```bash
    ps: 可安装桌面版，官方提供了可视化界面
    测试是否安装成功 `docker -v`
    ```
   
2. 克隆源码到目标服务器

3. 运行源码项目根目录下的start.sh即可

> 正常情况下执行docker-compose命令结束后 不会出现报错信息 后端服务启动成功
> 配置host <服务器主机IP> tcm.huobi.com 即可访问项目

# 服务器直接部署方式
1. 安装python

    
2. 安装Node.js
    请参考官网：<https://nodejs.org/en/download/>
    
3. 安装nginx
    请参考官网：<http://nginx.org/en/download.html> <https://www.nginx.com/>
    
    
4. 克隆源码到目标服务器   
    ```bash
    1) 在源码根目录下依次执行以下步骤
    pip3 install -r requirements.txt
    cd page && npm install && npm run build:prod
    2) 配置nginx
    修改源码根目录下nginx.conf文件的root为项目所在路径 + /page/dist（即npm编译后的静态文件生成路径）如文件中的示例
    将nginx.conf 拷贝至nginx的配置路径 如cp nginx.conf  /etc/nginx/conf.d/
   ps: 查看nginx配置地址 使用命令 nginx -t
   重新加载使新的配置生效 nginx -s reload
    ```

# 项目功能介绍
一、**团队管理**

1.1 **团队创建**

* 点击平台左侧“团队管理”菜单进入团队管理列表页面
* 点击【创建团队】按钮弹出创建团队弹窗（如图）
* 输入团队名称、团队描述，选择团队成员
* 点击【确定】创建团队
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-123112.png)

1.2 **团队编辑/删除**
* 创建团队者有权限可见团队操作按钮
* 点击团队右侧编辑按钮可编辑团队信息
* 点击删除可删除该条数据
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-123518.png)


二、**项目管理**

2.1 **创建项目**
* 点击左侧菜单栏“项目管理”打开项目管理列表页面
* 点击【创建项目】按钮弹出创建项目弹窗（如图所示）
* 上传项目logo文件、输入项目名称（项目名称最长支持25个字符长度，超过25不允许再输入）、输入项目描述、选择可见项目团队
* 点击【确定】创建项目
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-123616.png)

2.2 **项目编辑/删除**
* 项目创建者有权限可见项目操作按钮
* 点击项目列表中的编辑按钮可打开项目编辑弹窗编辑项目信息
* 点击删除可删除该条数据
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-123643.png)



三、 **用例管理**

3.1 **添加用例分组**
* 在项目管理页面中任意选择其中一个项目，点击后即可进入用例管理页面
* 点击第一级分组添加按钮弹出添加第一级分组的弹窗，输入分组名称，点击【确定】添加分组。
* 点击分组后面的添加按钮可以添加分组的下一级分组，分组最多添加至第4级别，第4级别分组将不再显示添加下一级分组按钮。
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-134630.png)


3.2 **编辑/删除用例分组**
* 鼠标悬浮至要编辑的用例分组名称上方，会显示编辑与删除按钮
* 点击编辑后输入更改内容，点击【确定】编辑分组名称，点击【取消】关闭弹框
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-134746.png)

3.3 **创建用例**
* 点击【创建用例】按钮 会打开创建用例页面
* 输入用例标题（标题长度最长20个字符，超过20字符不允许再输入）、
* 选择分组
* 可以添加标签或附件
* 点击新增或保存并下一条

NOTE:
用例标签是每个用例的的特殊标签，例如在创建用例时，加入标签“T12345”，则在搜索用例时，只需输入“T12345”就可将整个项目中所有包含有“T12345”的标签的用例检索出来。

![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-125924.png)


3.4 **编辑/复制用例**
* 鼠标hover到某个用例的标题上 会出现操作按钮 如下图
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/066B614F-2AEA-4E20-9494-DCD0F2B6B8A3.png)

3.5 **删除用例**
* 点击对应用例的删除按钮（如图所示）删除用例
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-140754.png)

3.6 **查看用例历史记录**
* 点击对应用例的查看历史按钮（如图所示）查看用例历史操作记录
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-140730.png)


3.7 **批量导入/导出用例**
* 点击批量操作按钮，
* 选择“下载模板文件”，打开模板，编辑用例信息，选择“导入Excel”，选中要上传的用例文件，弹出待导入用例信息弹窗（如图2.6.14.2所示），点击【开启导入】按钮导入用例，点击【关闭窗口】取消导入
* 导入的用例若有不符合要求的字段时，页面会标记并提示出来
* 点击批量操作按钮，选择“导出Excel”，将此项目下的全部用例以Excel表格形式下载到本地，表格名称以时间命名
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-141114.png)


3.8 **脑图模式**
* 在用例管理页面中点击切换用例模式即可进入脑图模式
* 涵盖了xmind的基本功能 添加、编辑、删除节点等 支持导入 导出 
* 更多功能可自行探索
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-141439.png)


四、 **测试计划**

4.1 **创建测试计划/里程碑**
* 进入任意一个项目页面，普通模式下点击左侧【测试计划】--创建按钮 选择里程碑/测试计划 输入相关表单信息 确定即可
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-125126.png)
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-125537.png)


4.2 **编辑/复制测试计划**
* 选择任意一个测试计划 点击编辑/复制/归档 会弹出对应的表单信息 根据提示输入相关信息 点击确定即可完成操作
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-142544.png)


4.3 **修改用例分配人员/优先级**
单个修改：点击对应用例分配人员按钮，选择要分配的人员
批量修改：选中多个用例，点击【分配给】/【优先级】，根据提示操作即可
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-143028.png)


4.4 **开始测试**
* 点击测试计划信息页面右上角【开始测试】按钮进入计划测试页面
* 可以输入用例关键字过滤或勾选【只测我的】
* 右侧页面有【编辑用例】和【新建用例】便捷入口 新增后会增加一条用例且关联到该测试计划中
* 右下角 【通过并下一条】或点击展开 失败并下一条等可修改用例的执行结果
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-145441.png)


4.5 **记录测试**
* 点击【记录结果】按钮展示“记录测试结果”弹窗，选择测试结果状态，输入测试结果，点击【添加结果】按钮添加结果。
* 如果有缺陷，点击【添加缺陷】按钮弹出“添加缺陷”弹窗，输入缺陷信息，点击【添加】按钮添加缺陷；
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-145839.png)

点击【添加备注】按钮，输入备注信息，点击【添加备注】可进行备注添加，点击【添加备注并下一条】可进行备注添加同时打开新的备注添加输入框，添加新的备注


五、**测试报告**

5.1 **创建测试报告**
点击项目管理中心页面左侧菜单“测试报告”进入测试报告页面。点击【创建报告】按钮弹出“创建报告”弹窗（如图所示），选择里程碑，选择里程碑对应的测试计划，修改报告名称，点击【确定】按钮创建测试报告。
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-131326.png)


5.2 **查看/删除报告**
点击对应测试报告操作按钮【查看报告】，跳转至测试报告详情页面（如图）
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-131403.png)
![image](https://raw.githubusercontent.com/zhangqiuhong/hb_case_management/master/image/WX20210304-131348.png)


> 平台内包含很多功能等待使用者自行探索 在此不详细介绍了 
> 


# Contributors
- guoliang ([@github](https://github.com/guoliang))
- zhangqiuhong ([@github](https://github.com/zhangqiuhong))
- yuli ([@yuli])


## 其他优秀的项目
- [飞蛾](https://feie.work/) 

