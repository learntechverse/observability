# ELK Stack Installation & Setup on Windows
Together, these tools enable you to aggregate logs from different sources, analyze the data, and create visualizations that help in monitoring and troubleshooting your applications.

# Setting Up ELK Stack

## Prerequisites

- Java Development Kit (JDK) 8 or 11
- Sufficient system resources (CPU, RAM, and disk space)

## Installation on Windows

### 1. Download Elasticsearch

- Go to the [Elasticsearch download page](https://www.elastic.co/downloads/elasticsearch) and download the Windows zip package.
- Extract the zip file to a directory, for example `C:\elasticsearch`.

### 2. Configure Elasticsearch

- Open `C:\elasticsearch\config\elasticsearch.yml` in a text editor.
- Set `cluster.name` and `node.name` as follows:
  ```yaml
  cluster.name: my-elk-cluster
  node.name: node-1
- Adjust other settings like `network.host` to bind to an IP address if needed.

## 3. Run Elasticsearch
- Open a Command Prompt as Administrator.
- Navigate to the bin directory of your Elasticsearch installation: `cd C:\elasticsearch\bin`
- Start Elasticsearch: `elasticsearch.bat`

## 4. Download Logstash
- Go to the [Logstash download page](https://www.elastic.co/downloads/logstash) and download the Windows zip package.
- Extract the zip file to a directory, for example C:\logstash.

## 5. Configure Logstash
- Create a configuration file, for example C:\logstash\config\logstash.conf, with the following content:
```yaml
    input {
    file {
        path => "C:/path/to/your/logfile.log"
        start_position => "beginning"
    }
    }
    output {
    elasticsearch {
        hosts => ["http://localhost:9200"]
    }
    stdout { codec => rubydebug }
    }
```

## 6. Run Logstash
- Open a new Command Prompt as Administrator.
- Navigate to the bin directory of your Logstash installation: `cd C:\logstash\bin`
- Start Logstash with your configuration file: `logstash.bat -f C:\logstash\config\logstash.conf`

## 7. Download Kibana
- Go to the Kibana download page and download the Windows zip package.
- Extract the zip file to a directory, for example C:\kibana.