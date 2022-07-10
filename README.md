# ant-xiaomisport
利用ant本地实现每天自动刷微信运动步数  
**首先需要手机下载小米运动App，注册账号，绑定微信运动**
## 使用方法
然后需要从官网下载apache ant，地址为： http://ant.apache.org/bindownload.cgi ；安装比较简单，就是解压配置环境变量就好了和安装jdk差不多。（在环境变量配置窗口中的“用户变量”中新增一个变量名为ANT_HOME，值为Ant解压后的目录，然后在“用户变量”下找PATH变量，如果没有就新增一个PATH变量，如果有就直接在PATH变量中加入新的值，值为“%ANT_HOME%\bin”最后在cmd中执行ant -version测试）    
这个代码在项目中直接运行也是可以的，只是不能实现每天自动运行。  
## 项目结构与配置 ##  
这里面有几点要注意的地方：  
1、你只需要改的地方就是classname和classpath里面的值  
2、classname里面的值是项目里的类名（需要带项目路径，不带后缀java）  
这里我的XiaoMiSportUtils类的绝对路径是：D:\Java\IdeaProjects\new-ew-cloud\yunjl-ant-xiaomisport\src\main\java\yunjl\xiaomisport\XiaoMiSportUtils.java  
因为是在项目里，且项目的package是 yunjl.xiaomisport ，所以我的classname的值就是yunjl.xiaomisport.XiaoMiSportUtils，你们要是自己建项目的话这个要注意，要不然后面运行类的时候会报错找不到这个类  
3、classpath的值就是java类编译后（.class）的绝对路径了（不是java类的）最简单的办法就是在项目中运行一下，会出现这个target\classes\yunjl\xiaomisport\XiaoMiSportUtils.class文件  
复制这个文件的绝对路径，去掉package路径，我的绝对路径是：D:\Java\IdeaProjects\new-ew-cloud\yunjl-ant-xiaomisport\target\classes\yunjl\xiaomisport\XiaoMiSportUtils.class  
所以我填的值就是：D:\Java\IdeaProjects\new-ew-cloud\yunjl-ant-xiaomisport\target\classes  
4、因为这个项目引入了hutool包，所以运行的时候也要指定jar包的绝对路径位置：在classpath值中填就行了，以；分隔  
到这就已经成功一大半了，可以测试下；进入build.xml文件的目录，cmd打开命令行窗口，输入ant回车  
出现刷入成功就代表成功了，可以去微信运动查看。  
成功的话改下bat文件：  
```batsh
ant -f D:\Java\IdeaProjects\xx-SpringCloud\xx-ant\src\main\java\yunjl\xioamisport\build.xml>D:\Java\IdeaProjects\xx-SpringCloud\xx-ant\src\main\java\yunjl\xioamisport\run.log
```  
用自己的build.xml文件的绝对路径替换掉我的，后面的路径就是一个输出日志，随便搞个位置都行，我放在了本层目录，运行后就会生成一个run.log文件  
