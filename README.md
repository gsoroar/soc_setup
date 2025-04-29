# Automated SOC Environment Setup Script

## Introduction


<img width="100%" alt="SOC Banner" src="https://github.com/gsoroar/soc_setup/blob/main/assets/soc_banner.jpeg?raw=true">

Building a secure monitoring environment from scratch can be time-consuming and complex. This script simplifies the process by automatically setting up an integrated Security Operations Center (SOC) environment including SIEM, NIDS, and HIDS on a single server. Designed for ease of use, it helps both beginners and advanced users deploy a functional SOC in minimal time.

**Important:** All services SIEM, NIDS, and HIDS — will run together on the same machine.

## What's Included

The script installs and configures the following components:

1. **SIEM (Security Information and Event Management):** Combines Elasticsearch, Kibana, and Filebeat to collect, visualize, and analyze security events.

- Elasticsearch 7.17.13 for indexing and search
- Kibana 7.17.13 for dashboard visualization
- Filebeat 7.17.13 for log forwarding

These versions are selected specifically for seamless integration with Wazuh Manager 4.5.

   <img width="443" alt="siem_setup_1" src="https://github.com/samiul008ghub/soc_setup/assets/54459574/94403da5-27bf-4afd-b95a-26eb548b5734">

   

   <img width="918" alt="elasticsearch" src="https://github.com/samiul008ghub/soc_setup/assets/54459574/31be9f30-ebed-49ae-8eed-807c70945eb0">


2. **NIDS (Network-based Intrusion Detection System):** Deploys Suricata, a robust intrusion detection engine, to monitor network traffic for malicious behavior.
**Important:** Suricata inspects traffic on the server's local network interface. To capture broader network traffic, connect the system to a TAP device or configure a SPAN port.

<img width="439" alt="Suricata_setup" src="https://github.com/samiul008ghub/soc_setup/assets/54459574/4e1f2e75-3ccc-4976-b976-178a068c92c5">

<img width="957" alt="suricata_dashboard" src="https://github.com/samiul008ghub/soc_setup/assets/54459574/7e5388da-a104-4807-a008-67bd0d289ee7">

3. **HIDS (Host-based Intrusion Detection System):** Installs Wazuh Manager (v4.5) to monitor activities and detect anomalies at the host level, providing an additional layer of security.

   
<img width="399" alt="wazuh_setup" src="https://github.com/samiul008ghub/soc_setup/assets/54459574/37c42fe1-665b-41c5-9d1b-7209472e9c08">



<img width="929" alt="wazuh" src="https://github.com/samiul008ghub/soc_setup/assets/54459574/5e6535fc-e082-43d4-861b-cc70cee0302e">

## Minimum System Requirements

Ensure your server meets these baseline specifications before proceeding:

- **Operating System:** Ubuntu (latest LTS recommended)
- **Memory:** 4 GB RAM or higher
- **Storage:** Minimum 20 GB free disk space

If your system doesn't meet these requirements, the script will issue a warning and allow you to proceed at your own risk.

## Usage

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/samiul008ghub/soc_setup/

2. Navigate to the repository's directory:
   ```bash
   cd soc_setup
3. Make the setup_script.sh executable:
   ```bash
   chmod +x setup_script.sh
4. Execute the setup_script.sh:
   ```bash
   ./setup_script.sh
5. Follow the on-screen prompts to choose which components you want to install and continue with the setup.
   Post-Installation Steps
6. After successfully running the script and completing the NIDS (Suricata) setup, consider the following post-installation steps:

##After Installation
## Checking Suricata Logs: 
- Confirm Suricata is running by inspecting /var/log/suricata/eve.json.
- Verify real-time event visualization by accessing the Suricata Dashboard in Kibana.

## Deploying Wazuh Agents: 
- For complete endpoint monitoring, install the Wazuh Agent on additional Linux and Windows machines.
- Agents feed host-level logs into the central SIEM system, improving visibility and detection capabilities.

## Best Practices & Recommendations
- **Backup First:** Before running the script, back up your system, especially in production environments.
- **Secure Your Environment:** After installation, apply system hardening techniques, configure firewall policies, and encrypt sensitive information to strengthen your overall security posture.






   

