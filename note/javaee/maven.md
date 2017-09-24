MyEclipse里面有自带的maven，由于某某原因，不用自带的maven。  
安装maven
1.下载maven包，解压到某路径。（该路径为安装路径）我的是D:\maven-3.0.4 2.配置环境变量 MAVEN_HOME =D:\maven-3.0.4 path = %MAVEN_HOME%\bin 3.打开 cmd，在里面敲：mvn -version，打印出版本信息，说明安装成功。
配置仓库位置
找到安装路径下的conf/settings.xml 配置文件 <localRepository>仓库路径</localRepository>
MyEclipse配置maven
myeclipse 本身已经集成 maven 插件，我们只是简单的配置一下即可 Window –> Preferences –> MyEclipse –> Maven4MyEclipse –> Installations，点击add选择maven安装路径 Window –> Preferences –> MyEclipse –> Maven4MyEclipse –>User Settings，选择之前配置的settings.xml文件 Window->Preferences->Java->Installed JREs。编辑选择的JRE，在Default VM Arguments输入-Dmaven.multiModuleProjectDirectory=$MAVEN_HOME
其他
eclipse中使用maven插件的时候，运行run as maven build的时候报错 -Dmaven.multiModuleProjectDirectory system propery is not set. Check $M2_HOME environment variable and mvn script match. 然后在Window->Preference->Java->Installed JREs->Edit 在Default VM arguments中设置 -Dmaven.multiModuleProjectDirectory=$MAVEN_HOME 1：maven 2.1默认用jdk 1.3来编译，maven 3 貌似是用jdk 1.5，如果项目用的jdk 1.6也会有问题，compiler插件可以指定JDK版本为1.6。