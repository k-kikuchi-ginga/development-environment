# FROM centos
FROM centos:centos7

# インストール済みのパッケージをアップデート＆キャッシュのクリア
RUN yum -y update && yum clean all


# 言語を日本語に設定
RUN localedef -i ja_JP -f UTF-8 ja_JP.UTF-8
RUN echo 'LANG="ja_JP.UTF-8"' >  /etc/locale.conf
ENV LANG ja_JP.UTF-8


# 日付を日本語に設定
RUN echo 'ZONE="Asia/Tokyo"' > /etc/sysconfig/clock 
RUN rm -f /etc/localtime
RUN ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime


# manをインストールする前に、manファイルをインストールするように設定変更
RUN sed -i -e"s/^tsflags=nodocs/\# tsflags=nodocs/" /etc/yum.conf


# manと、man-pagesをインストール
RUN yum -y install man
RUN yum -y install man-pages.noarch
RUN yum -y install man-pages-ja.noarch

#キャッシュクリア
#RUN yum clean all

#"Development and Creative Workstation"グループのインストール
#RUN yum clean all
RUN yum -y install deltarpm
RUN yum -y groupinstall "Development and Creative Workstation"

# Javaダウンロード
# RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
#  http://download.oracle.com/otn-pub/java/jdk/8u191-b12/2787e4a523244c269598db4e85c51e0c/jdk-8u191-linux-x64.rpm \
#  -O /tmp/jdk-8u191-linux-x64.rpm 
# RUN yum localinstall -y /tmp/jdk-8u191-linux-x64.rpm
RUN yum install -y java-1.8.0-openjdk java-1.8.0-openjdk-devel
ENV JAVA_HOME /usr/lib/jvm/java-1.8.0-openjdk
ENV PATH $PATH:$JAVA_HOME/bin

#STSダウンロード
RUN wget -q -O /tmp/spring-tool-suite-4-4.0.0.RELEASE-e4.9.0-linux.gtk.x86_64.tar.gz "http://download.springsource.com/release/STS4/4.0.0.RELEASE/dist/e4.9/spring-tool-suite-4-4.0.0.RELEASE-e4.9.0-linux.gtk.x86_64.tar.gz"
RUN tar xavf /tmp/spring-tool-suite-* -C /opt/
RUN ln -s /opt/sts-4.0.0.RELEASE /usr/bin
