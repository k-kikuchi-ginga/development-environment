FROM centosjp

#キャッシュクリア
RUN yum clean all

#"Development and Creative Workstation"グループのインストール
RUN yum clean all
RUN yum -y install deltarpm
RUN yum -y groupinstall "Development and Creative Workstation"

#Javaダウンロード
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
 http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/jdk-8u181-linux-x64.rpm \
 -O /tmp/jdk-8u181-linux-x64.rpm 
RUN yum localinstall -y /tmp/jdk-8u181-linux-x64.rpm

#STSダウンロード
RUN wget -q -O /tmp/spring-tool-suite-4-4.0.0.RELEASE-e4.9.0-linux.gtk.x86_64.tar.gz "http://download.springsource.com/release/STS4/4.0.0.RELEASE/dist/e4.9/spring-tool-suite-4-4.0.0.RELEASE-e4.9.0-linux.gtk.x86_64.tar.gz"
RUN tar xavf /tmp/spring-tool-suite-* -C /opt/
RUN ln -s /opt/sts-4.0.0.RELEASE /usr/bin
