# Itlittlewhite.gethub.io
lxy的个人博客
最近刚刚入职，学习公司的artery框架，当做笔记记一下

前期准备：


构建查询列表基本步骤：
1.构造页面（布局）

新建表单
新增列表区域
增加字段控件（相关表，设置数据源）
2.数据源查询（logic）
在java编写，通过调用service返回结果
字段的数据源处与pojo类中的属性名称相同即可。



新增表单基本步骤：
构造页面（布局）：

新建表单
弹出窗口（linkto/Artery.openForm）
新增表单区域
增加字段控件
相关表
设置提交名称
配置单值代码（部署后的项目路径/ptmodule/arteryPiatform找到对应配置文件）
客户端脚本：

提交表单信息
*两种提交方式：

//1.适用于多字段，有对应的pojo类时使用
form.sunmit(function(result){});

//2.适用于字段较少时，可以直接通过rc.put传递参数
 rc.put("" : "");
 rc.send(function(result){});*
1
2
3
回调解析后台返回结果

function(result){}//result与后台的返回值对应
              Artery.showInfo("XXXX"):void
              Artery.showError("XXXX"):void
1
2
3
刷新查询列表
//新增后的数据更新到列表中
Artery.fet(listArea).reload();
1
2
获得父页面控件
//获得父窗口组件
Artery.getWin().get(str id);
//关闭弹出窗口
Artery.getWin().close();
1
2
3
4
服务器端脚本（保存）：

获得参数封装
获得表单提交数据：

ArteryParamUtil.getPojo(Class cls ,String name);

获得单独传递的参数：

 ArteryParamUtil.getString(key);//字符串
 ArteryParamUtil.getInt(key);//整数
 ...
1
2
3
保存到数据库
用对应的service调用对应的方法，实现保存
返回成功标识
修改表单基本步骤：
构造页面：
共用新增页面延用布局
表单区域上配置数据源
字段同样配置数据源（同列表区域中的字段）
增加字段控件（同新增）
弹出窗口
linkto
Artery.openForm
传递参数
客户端脚本-提交：（不变，与新增相同）

服务器端脚本（保存）：

获得参数，封装
保存到数据库
共用新增保存，判断是否有主键。
返回成功标识
删除基本步骤：
客户端脚本：

删除提示
Artery.confirmMsg("XX");
1
传递参数
@param的形式获得图书ID
         rc.put("" : "");
        rc.send(function(result){});*
1
2
3
回调展示删除结果
//结果提示&刷新列表
Artery.showInfo("XXXXX");
Artery.get("name").reload();
1
2
3
服务器端脚本：

获得参数
调用删除方法，从库中删除
返回成功标识
--------------------- 
作者：挨踢小小白 
来源：CSDN 
原文：https://blog.csdn.net/weixin_41815286/article/details/89327165 
版权声明：本文为博主原创文章，转载请附上博文链接！
