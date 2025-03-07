# SIEM Project using ELK Stack and Packetbeat on Windows

## Overview
This project is a Security Information and Event Management (SIEM) setup using the ELK Stack (Elasticsearch, Logstash, and Kibana) along with Packetbeat for network traffic monitoring on Windows. The goal is to collect, analyze, and visualize network and system logs for security monitoring and threat detection.

## Tools Used
- **Elasticsearch** – Stores and indexes logs.
- **Logstash** – Processes and forwards logs to Elasticsearch.
- **Kibana** – Visualizes logs and data.
- **Packetbeat** – Captures and sends network traffic logs to Elasticsearch.

## Installation and Setup

### 1. Install ELK Stack on Windows
1. Download and install **Elasticsearch, Logstash, and Kibana** from the official Elastic website.
2. Configure Elasticsearch (`elasticsearch.yml`):
   ```yaml
   network.host: localhost
   http.port: 9200
   ```
3. Start Elasticsearch using the command:
   ```powershell
   .\bin\elasticsearch.bat
   ```
4. Configure Kibana (`kibana.yml`):
   ```yaml
   server.host: "localhost"
   elasticsearch.hosts: ["http://localhost:9200"]
   ```
5. Start Kibana:
   ```powershell
   .\bin\kibana.bat
   ```

### 2. Install and Configure Packetbeat
1. Download **Packetbeat** for Windows from the Elastic website.
2. Configure `packetbeat.yml` to send data to Elasticsearch:
   ```yaml
   output.elasticsearch:
     hosts: ["localhost:9200"]
   ```
3. Run Packetbeat:
   ```powershell
   .\packetbeat.exe setup
   .\packetbeat.exe -e
   ```

### 3. Visualizing Data in Kibana
1. Open Kibana in a browser: `http://localhost:5601`
2. Navigate to **Stack Management > Index Patterns** and create an index for `packetbeat-*`.
3. Go to **Discover** and explore network logs.
4. Use **Dashboards** to visualize network activities.

## Key Features
- Real-time network monitoring using Packetbeat.
- Centralized log management with Elasticsearch.
- Log parsing and processing using Logstash.
- Custom dashboards and visualization in Kibana.

## Future Improvements
- Add Filebeat and Winlogbeat for more log sources.
- Implement alerting mechanisms using **ElastAlert**.
- Improve threat detection with security rule sets.

## Conclusion
This SIEM project provides a basic setup for monitoring network traffic and logs using ELK Stack on Windows. It helps in identifying suspicious activities and gaining better visibility into network events.

Feel free to explore and improve the setup!

