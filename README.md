# SDN实验环境的搭建

------
主机:Ubuntu 16.04 、Mininet + Opendaylight控制器   依赖环境：Java 8-compliant JDK and Maven 3.1.1 or later


> * Mininet使用源码安装
> >  * 1.软件更新
        `apt-get update
        apt-get upgrade`
> >  * 2.从github上获取Mininet源码。
    `git clone git://github.com/mininet/mininet`
> >  * ３. 获取完以后，查看当前获取的Mininet版本
    `cd mininet
     cat INSTALL`
> >  * 4.  源码树获取成功以后，安装Mininet。
    ` mininet/util/install.sh -a`
> >  * ５.安装完成以后，通过简单的命令测试Mininet的基本功能。
    `sudo mn --test pingall`
    并查看当前版本
    `mn --version`

>  安装完成


> * OpenDayLight 安装</br>
>> *  Java 8 </br>
    >>> * 1.增加Java8库</br>
    `sudo add-apt-repository ppa:webupd8team/java`</br>
    `sudo apt-get update`</br>
   `sudo apt-get install oracle-java8-installer
    `</br>
    >>>  * 2.检验Java版本并安装</br>
    `sudo apt-get install oracle-java8-set-default`</br>
    安装成功后检查版本是否正确</br>
    `java -version `</br>
    >>>  * 3.增加环境变量</br>
    `cat >> /etc/environment <<EOL`</br>
   ` JAVA_HOME=/usr/lib/jvm/java-8-oracle`</br>
    `JRE_HOME=/usr/lib/jvm/java-8-oracle/jre`</br>
    `EOL`</br>
    
>> * Maven 3 </br>
    >>>* 1.首先安装Java 8 （参上),下载安装包</br> 
    ` cd /usr/local`</br>
    `wget http://www-eu.apache.org/dist/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.tar.gz`</br>
    安装完成之后解压</br>
    `sudo tar xzf apache-maven-3.5.2-bin.tar.gz`</br>
    `sudo ln -s apache-maven-3.5.2 apache-maven`</br>
     >>>* 2.设置环境变量
     `sudo vi /etc/profile.d/apache-maven.sh`<br/>
     增加
     `export JAVA_HOME=/usr/lib/jvm/java-8-oracle`<br/>`export M2_HOME=/usr/local/apache-maven`<br/>`export MAVEN_HOME=/usr/local/apache-maven`<br/>`export PATH=${M2_HOME}/bin:${PATH}`<br/>
     加载sh
     `source /etc/profile.d/apache-maven.sh`
     >>>* 3.验证安装
     `mvn -version `
     最后删除安装包（可选择不删除）
     `rm -f apache-maven-3.5.2-bin.tar.gz`
     
>> * Opendaylight Carbon 安装
    和beryllium的安装类似  在fearture:install 的时候如果没有找到包 先:list -a | grep 查找一下
    
    feature:install odl-restconf
    feature:install odl-l2switch-switch-ui
    feature:install odl-openflowplugin-flow-services-he
    feature:install odl-openflowplugin-flow-services-ui
    feature:install odl-dluxapps-applications
    feature:install odl-dluxapps-yangutils
