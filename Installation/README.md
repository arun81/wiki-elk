# Installing ELK stack on Centos 7

## Prepare OS
```
yum install -y epel-release wget
yum -y update
```

## Install Java Runtime Environment (JRE)
 
## Install Elastic YUM repositories  
```
rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch

cat << EOF > /etc/yum.repos.d/elasticsearch.repo
[elasticsearch-5.x]
name=Elasticsearch repository for 5.x packages
baseurl=https://artifacts.elastic.co/packages/5.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md
EOF
 
cat << EOF > /etc/yum.repos.d/logstash.repo
[logstash-5.x]
name=Elastic repository for 5.x packages
baseurl=https://artifacts.elastic.co/packages/5.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md
EOF
 
cat << EOF > /etc/yum.repos.d/kibana.repo
[kibana-5.x]
name=Kibana repository for 5.x packages
baseurl=https://artifacts.elastic.co/packages/5.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md
EOF
```

## Install Elasticsearch
``` 
yum -y install elasticsearch
``` 

## Install Logstash 
``` 
yum install -y logstash
``` 
## Install Kibana 
``` 
yum install -y kibana
```
 
## Enable and start services for ELK stack 
``` 
systemctl start elasticsearch.service
systemctl enable elasticsearch.service
systemctl start logstash.service
systemctl enable logstash.service
systemctl start kibana.service
systemctl enable kibana.service
``` 
