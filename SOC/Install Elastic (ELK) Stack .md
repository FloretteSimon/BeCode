MOSTLY COPY FROM VIDEO WEBSITE 
https://www.youtube.com/watch?v=bb-FXjIq-8w
https://portforwarded.com/install-elastic-elk-stack-8-x-on-ubuntu-22-04-lts/

## 1. Update our repos and packages:

sudo apt update && sudo apt upgrade -y  


## 2. Download and install the public key for elastic search:

wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg


## 3. Install the apt package that allows https package downloads:

sudo apt-get install apt-transport-https


## 4. Save the repo in the elastic sources list

echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list


## 5. Then update apt again and install Elastic Search:

sudo apt-get update && sudo apt-get install elasticsearch


## 6. Open the Elastic configuration file:

sudo nano /etc/elasticsearch/elasticsearch.yml


## 7. To make the service accessible from anywhere on the network, change the network host from localhost to 0.0.0.0 and uncomment if necessary:

networkhost 0.0.0.0


## 8. Set the security feature from true to false:

xpack.security.enabled false


## 9. Enable and start the service:

sudo systemctl enable elasticsearch && sudo systemctl start elasticsearch


## 10. From there you can check the status:

sudo systemctl status elasticsearch


## 11. And verify the server is responding to queries:

curl -XGET "localhost:9200"


## 12. Install Logstash (Logstash is an open-source data processing pipeline that ingests, transforms, and sends data to various outputs, commonly used with Elasticsearch and Kibana in the ELK stack.):

sudo apt install logstash



IMPORTANT: Several resources on configuring Logstash don’t mention you need to set proper filters. We will be sending system and Apache server logs from our web installation to Logstash, and if we don’t set filters, Logstash will receive the data but won’t know what to do with it. You’ll get the notification in Kibana that you have data, but it will be empty! 

## 13. Create a filter in Logstash for the Filebeat data we’re sending. Open up a filter file:

sudo nano /etc/logstash/conf.d/beats.conf


## 14. Configure the file as seen below. The input specifies the port number logstash will accept input from, and the filters needed to parse the data we’re looking for. The output specifies that we want to send the data to elastic search for indexing:

input {
  beats {
    port => 5044
  }
}

filter {
  if [type] == "syslog" {
    grok {
      match => { "message" => "%{SYSLOGLINE}" }
    }
    date {
      match => [ "timestamp", "MMM  d HH:mm:ss", "MMM dd HH:mm:ss" ]
    }
  }

  if [type] == "apache" {
    grok {
      match => { "message" => "%{COMBINEDAPACHELOG}" }
    }
    date {
      match => [ "timestamp", "dd/MMM/yyyy:HH:mm:ss Z" ]
    }
  }
}

output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "%{[@metadata][beat]}-%{+YYYY.MM.dd}"
  }
}

Save the file. 

## 15. Enable and start Logstash:

sudo systemctl enable logstash && sudo systemctl start logstash


## 16. Check Logstash’s status with:

sudo systemctl status logstash


## 17. Install Kibana (Kibana is an open-source visualization and analytics tool that allows users to explore, visualize, and interact with data stored in Elasticsearch.):

sudo apt install kibana


## 18. Open Kibana’s configuration file:

sudo nano /etc/kibana/kibana.yml


## 19.Uncomment and change the following as needed, then save the file:

server.port 5601

server.host "0.0.0.0"

elasticsearch.hosts: ["http://localhost:9200"]

<img width="919" alt="Capture d’écran 2024-08-21 à 11 11 50" src="https://github.com/user-attachments/assets/7e70a6c7-2983-4f2e-9900-195c2d6ee9f1">

<img width="930" alt="Capture d’écran 2024-08-21 à 11 12 19" src="https://github.com/user-attachments/assets/710f2745-f8c9-4732-ad72-4bcc7dfe5558">


## 20. Enable and start Kibana:

sudo systemctl enable kibana && sudo systemctl start kibana


## 21. And check Kibana’s status with:

sudo systemctl status kibana


## 22. Go browser:

ip:5601/app/home#/

<img width="936" alt="Capture d’écran 2024-08-21 à 11 14 30" src="https://github.com/user-attachments/assets/573b3616-8fcb-4976-b679-34b8a9647b44">
