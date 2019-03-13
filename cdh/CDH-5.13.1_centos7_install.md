# CDH-5.13.1_centos7_install

## һ������
* ϵͳ:centos7
* ����:8��/16G�ڴ�/100GӲ�� ������
* ��������:3̨������

## �������谲װ��
1. CM��:
http://archive.cloudera.com/cm5/cm/5/cloudera-manager-centos7-cm5.13.1_x86_64.tar.gz
2. PARCEL����
http://archive.cloudera.com/cdh5/parcels/5.13.1/CDH-5.13.1-1.cdh5.13.1.p0.2-el7.parcel
http://archive.cloudera.com/cdh5/parcels/5.13.1/CDH-5.13.1-1.cdh5.13.1.p0.2-el7.parcel.sha1
http://archive.cloudera.com/cdh5/parcels/5.13.1/manifest.json
3. java-mysql����jar����
http://central.maven.org/maven2/mysql/mysql-connector-java/5.1.22/mysql-connector-java-5.1.22.jar

## ����������������
1. ������
	* 3̨�������޸�/etc/sysconfig/network������������(hadoop01,hadoop02,hadoop03)
	* hostname hadoop01 // hostname hadoop02 // hostname hadoop03
2. hosts����
	* 3̨�����޸�hosts��
		* 192.168.*.* hadoop01
		* 192.168.*.* hadoop02
		* 192.168.*.* hadoop03
3. ssh���ܵ�¼
	* 3̨��������ssh���ܵ�¼
		* ssh-keygen
		* ssh-copy-id hadoop01
		* ssh-copy-id hadoop02
		* ssh-copy-id hadoop03
4. jdk����ȷ��
	* echo $JAVA_HOME ����
	* java --version ȷ��jdk��������
5. ��װntp
	* yum install ntp -y
	* systemctl start ntpd.service����#��������
	* systemctl enable ntpd.service����#����Ϊ��������
6. �رշ���ǽ
	* systemctl stop firewalld.service #ֹͣfirewall
	* systemctl disable firewalld.service #��ֹfirewall��������
7. yum��װ
	* yum install -y chkconfig python bind-utils psmisc libxslt zlib sqlite cyrus-sasl-plain cyrus-sasl-gssapi fuse fuse-libs redhat-lsb bzip2
8. ����
	* (1) echo never > /sys/kernel/mm/transparent_hugepage/defrag
	* (2) echo never > /sys/kernel/mm/transparent_hugepage/enabled
	* vim /etc/rc.local #��(1),(2)������ӽ�ȥ
	
	* sysctl vm.swappiness=10
	* vim /etc/sysctl.conf ���vm.swappiness=10
	
	* setenforce 0
	* vim /etc/selinux/config  #��SELINUX=enforcing��ΪSELINUX=disabled�����ùر�
	
	
	
	