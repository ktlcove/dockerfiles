FROM centos:latest

RUN yum -y install wget apr-devel openssl-devel && \
    cd /tmp && \
    curl -L -O -s http://mirrors.tuna.tsinghua.edu.cn/apache/tomcat/tomcat-8/v8.5.35/bin/apache-tomcat-8.5.35.tar.gz && \
    wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2Ftechnetwork%2Fjava%2Fjavase%2Fdownloads%2Fjdk8-downloads-2133151.html; oraclelicense=accept-securebackup-cookie;" "https://download.oracle.com/otn-pub/java/jdk/8u191-b12/2787e4a523244c269598db4e85c51e0c/jdk-8u191-linux-x64.tar.gz" &> /dev/null && \
    tar zxf apache-tomcat-8.5.35.tar.gz -C /usr/local && \
    tar zxf jdk-8u191-linux-x64.tar.gz -C /usr/local && \
    ln -s /usr/local/apache-tomcat-8.5.35 /usr/local/tomcat && \
    ln -s /usr/local/jdk1.8.0_191 /usr/local/java && \
    echo 'export JAVA_HOME=/usr/local/java' >> /usr/local/tomcat/bin/setenv.sh && \
    # echo 'export JAVA_OPTS="$JAVA_OPTS -Djava.security.egd=file:/dev/./urandom"' >> /usr/local/tomcat/bin/setenv.sh && \
    echo 'export PATH=$JAVA_HOME/bin:$PATH' >> /usr/local/tomcat/bin/setenv.sh && \
    # echo 'export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar' >> /usr/local/tomcat/bin/setenv.sh && \
    chmod +x /usr/local/tomcat/bin/setenv.sh  && \
    sed -ri 's/FINE/ALL/g' /usr/local/tomcat/conf/logging.properties && \
    sed -ri 's/INFO/ALL/g' /usr/local/tomcat/conf/logging.properties && \
    # sed -ri '/AprLifecycleListener/d' /usr/local/tomcat/conf/server.xml && \
    # sed -ri '/AJP\/1.3/d' /usr/local/tomcat/conf/server.xml && \
    # sed -ri 's/appBase="webapps"/appBase="webapps" deployOnStartup="true"/g' /usr/local/tomcat/conf/server.xml && \
    # rm -rf /usr/local/tomcat/webapps/examples && \
    cat /usr/local/tomcat/bin/setenv.sh && \
    rm -rf /tmp/* && yum clean all

EXPOSE 8080

CMD ["/usr/local/tomcat/bin/catalina.sh", "run"]
