---
title: Connect data sources to Azure Sentinel | Microsoft Docs
description: Learn how to connect data sources like Microsoft 365 Defender (formerly Microsoft Threat Protection), Microsoft 365 and Office 365, Azure AD, ATP, and Cloud App Security to Azure Sentinel.
services: sentinel
documentationcenter: na
author: yelevin
manager: rkarlin
editor: ''

ms.service: azure-sentinel
ms.subservice: azure-sentinel
ms.devlang: na
ms.topic: how-to
ms.custom: mvc
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/01/2020
ms.author: yelevin

---
# Connect data sources

Once you have enabled Azure Sentinel, the first thing you need to do is connect your data sources. Azure Sentinel comes with a number of connectors for Microsoft solutions, available out of the box and providing real-time integration, including Microsoft 365 Defender (formerly Microsoft Threat Protection) solutions, Microsoft 365 sources (including Office 365), Azure AD, Microsoft Defender for Identity (formerly Azure ATP), Microsoft Cloud App Security, and more. In addition, there are built-in connectors to the broader security ecosystem for non-Microsoft solutions. You can also use Common Event Format (CEF), Syslog or REST-API to connect your data sources with Azure Sentinel.

1. On the menu, select **Data connectors**. This page lets you see the full list of connectors that Azure Sentinel provides and their status. Select the connector you want to connect and select **Open connector page**. 

   ![Data connectors gallery](./media/collect-data/collect-data-page.png)

1. On the specific connector page, make sure you have fulfilled all the prerequisites and follow the instructions to connect the data to Azure Sentinel. It may take some time for the logs to start syncing with Azure Sentinel. After you connect, you see a summary of the data in the **Data received** graph, and connectivity status of the data types.

   ![Configure data connectors](./media/collect-data/opened-connector-page.png)
  
1. Click the **Next steps** tab to get a list of out-of-the-box content Azure Sentinel provides for the specific data type.

   ![Next steps for connectors](./media/collect-data/data-insights.png)
 

## Data connection methods

The following data connection methods are supported by Azure Sentinel:

- **Service to service integration**:<br> Some services are connected natively, such as AWS and Microsoft services, these services leverage the Azure foundation for out-of-the box integration, the following solutions can be connected in a few clicks:
    - [Amazon Web Services - CloudTrail](connect-aws.md)
    - [Azure Active Directory](connect-azure-active-directory.md) - audit logs and sign-in logs
    - [Azure Activity](connect-azure-activity.md)
    - [Azure AD Identity Protection](connect-azure-ad-Identity-protection.md)
    - [Azure DDoS Protection](connect-azure-ddos-protection.md)
    - [Azure Defender for IoT](connect-asc-iot.md) (formerly Azure Security Center for IoT)
    - [Azure Information Protection](connect-azure-information-protection.md)
    - [Azure Firewall](connect-azure-firewall.md)
    - [Azure Security Center](connect-azure-security-center.md) - alerts from Azure Defender solutions
    - [Azure Web Application Firewall (WAF)](connect-azure-waf.md) (formerly Microsoft WAF)
    - [Cloud App Security](connect-cloud-app-security.md)
    - [Domain name server](connect-dns.md)
    - [Microsoft 365 Defender](connect-microsoft-365-defender.md) - includes MDATP raw data
    - [Microsoft Defender for Endpoint](connect-microsoft-defender-advanced-threat-protection.md) (formerly Microsoft Defender Advanced Threat Protection)
    - [Microsoft Defender for Identity](connect-azure-atp.md) (formerly Azure Advanced Threat Protection)
    - [Microsoft Defender for Office 365](connect-office-365-advanced-threat-protection.md) (formerly Office 365 Advanced Threat Protection)
    - [Office 365](connect-office-365.md) (now with Teams!)
    - [Windows firewall](connect-windows-firewall.md)
    - [Windows security events](connect-windows-security-events.md)

- **External solutions via API**: Some data sources are connected using APIs that are provided by the connected data source. Typically, most security technologies provide a set of APIs through which event logs can be retrieved.The APIs connect to Azure Sentinel and gather specific data types and send them to Azure Log Analytics. Appliances connected via API include:
    
    - [Alcide kAudit](connect-alcide-kaudit.md)
    - [Barracuda WAF](connect-barracuda.md)
    - [Barracuda CloudGen Firewall](connect-barracuda-cloudgen-firewall.md)
    - [BETTER Mobile Threat Defense](connect-better-mtd.md)
    - [Beyond Security beSECURE](connect-besecure.md)
    - [Citrix Analytics (Security)](connect-citrix-analytics.md)
    - [F5 BIG-IP](connect-f5-big-ip.md)
    - [Forcepoint DLP](connect-forcepoint-dlp.md)
    - [Okta SSO](connect-okta-single-sign-on.md)
    - [Orca Security](connect-orca-security-alerts.md)
    - [Perimeter 81 logs](connect-perimeter-81-logs.md)
    - [Proofpoint TAP](connect-proofpoint-tap.md)
    - [Qualys VM](connect-qualys-vm.md)
    - [Squadra Technologies secRMM](connect-squadra-secrmm.md)
    - [Symantec ICDX](connect-symantec.md)
    - [VMware Carbon Black Cloud Endpoint Standard](connect-vmware-carbon-black.md)
    - [Zimperium](connect-zimperium-mtd.md)


- **External solutions via agent**: Azure Sentinel can be connected via an agent to any other data source that can perform real-time log streaming using the Syslog protocol.

    Most appliances use the Syslog protocol to send event messages that include the log itself and data about the log. The format of the logs varies, but most appliances support CEF-based formatting for log data. 

    The Azure Sentinel agent, which is actually the Log Analytics agent, converts CEF-formatted logs into a format that can be ingested by Log Analytics. Depending on the appliance type, the agent is installed either directly on the appliance, or on a dedicated Linux-based log forwarder. The agent for Linux receives events from the Syslog daemon over UDP, but if a Linux machine is expected to collect a high volume of Syslog events, they are sent over TCP from the Syslog daemon to the agent and from there to Log Analytics.

    - **Firewalls, proxies, and endpoints - CEF:**
        - [AI Vectra Detect](connect-ai-vectra-detect.md)
        - [Check Point](connect-checkpoint.md)
        - [Cisco ASA](connect-cisco.md)
        - [Citrix WAF](connect-citrix-waf.md)
        - [CyberArk Enterprise Password Vault](connect-cyberark.md)
        - [ExtraHop Reveal(x)](connect-extrahop.md)
        - [F5 ASM](connect-f5.md)
        - [Forcepoint products](connect-forcepoint-casb-ngfw.md)
        - [Fortinet](connect-fortinet.md)
        - [Illusive Networks AMS](connect-illusive-attack-management-system.md)
        - [One Identity Safeguard](connect-one-identity.md)
        - [Palo Alto Networks](connect-paloalto.md)
        - [Trend Micro Deep Security](connect-trend-micro.md)
        - [Trend Micro TippingPoint](connect-trend-micro-tippingpoint.md)
        - [WireX Network Forensics Platform](connect-wirex-systems.md)
        - [Zscaler](connect-zscaler.md)
        - [Other CEF-based appliances](connect-common-event-format.md)
    - **Firewalls, proxies, and endpoints - Syslog:**
        - [Infoblox NIOS](connect-infoblox.md)
        - [Pulse Connect Secure](connect-pulse-connect-secure.md)
        - [Sophos XG](connect-sophos-xg-firewall.md)
        - [Symantec Proxy SG](connect-symantec-proxy-sg.md)
        - [Symantec VIP](connect-symantec-vip.md)
        - [Other Syslog-based appliances](connect-syslog.md)
    - DLP solutions
    - [Threat intelligence providers](connect-threat-intelligence.md)
    - [DNS machines](connect-dns.md) - agent installed directly on the DNS machine
    - [Azure Stack VMs](connect-azure-stack.md)
    - Linux servers
    - Other clouds
    
## Agent connection options<a name="agent-options"></a>

To connect your external appliance to Azure Sentinel, the agent must be deployed on a dedicated machine (VM or on premises) to support the communication between the appliance and Azure Sentinel. You can deploy the agent automatically or manually. Automatic deployment is only available if your dedicated machine is a new VM you are creating in Azure. 


![CEF in Azure](./media/connect-cef/cef-syslog-azure.png)

Alternatively, you can deploy the agent manually on an existing Azure VM, on a VM in another cloud, or on an on-premises machine.

![CEF on premises](./media/connect-cef/cef-syslog-onprem.png)

## Map data types with Azure Sentinel connection options


| **Data type** | **How to connect** | **Data connector?** | **Comments** |
|------|---------|-------------|------|
| AWSCloudTrail | [Connect AWS](connect-aws.md) | &#10003; | |
| AzureActivity | [Connect Azure Activity](connect-azure-activity.md) and [Activity logs overview](../azure-monitor/platform/platform-logs-overview.md)| &#10003; | |
| AuditLogs | [Connect Azure AD](connect-azure-active-directory.md)  | &#10003; | |
| SigninLogs | [Connect Azure AD](connect-azure-active-directory.md)  | &#10003; | |
| AzureFirewall |[Azure Diagnostics](../firewall/firewall-diagnostics.md) | &#10003; | |
| InformationProtectionLogs_CL  | [Azure Information Protection reports](/azure/information-protection/reports-aip)<br>[Connect Azure Information Protection](connect-azure-information-protection.md)  | &#10003; | This usually uses the **InformationProtectionEvents** function in addition to the data type. For more information, see [How to modify the reports and create custom queries](/azure/information-protection/reports-aip#how-to-modify-the-reports-and-create-custom-queries)|
| AzureNetworkAnalytics_CL  | [Traffic analytic schema](../network-watcher/traffic-analytics.md) [Traffic analytics](../network-watcher/traffic-analytics.md)  | | |
| CommonSecurityLog  | [Connect CEF](connect-common-event-format.md)  | &#10003; | |
| OfficeActivity | [Connect Office 365](connect-office-365.md) | &#10003; | |
| SecurityEvents | [Connect Windows security events](connect-windows-security-events.md)  | &#10003; | For the Insecure Protocols workbooks, see [Insecure protocols workbook setup](./quickstart-get-visibility.md#use-built-in-workbooks)  |
| Syslog | [Connect Syslog](connect-syslog.md) | &#10003; | |
| Microsoft Web Application Firewall (WAF) - (AzureDiagnostics) |[Connect Microsoft Web Application Firewall](./connect-azure-waf.md) | &#10003; | |
| SymantecICDx_CL | [Connect Symantec](connect-symantec.md) | &#10003; | |
| ThreatIntelligenceIndicator  | [Connect threat intelligence](connect-threat-intelligence.md)  | &#10003; | |
| VMConnection <br> ServiceMapComputer_CL<br> ServiceMapProcess_CL|  [Azure Monitor service map](../azure-monitor/insights/service-map.md)<br>[Azure Monitor VM insights onboarding](../azure-monitor/insights/vminsights-enable-overview.md) <br> [Enable Azure Monitor VM insights](../azure-monitor/insights/vminsights-enable-overview.md) <br> [Using Single VM On-boarding](../azure-monitor/insights/vminsights-enable-portal.md)<br>  [Using On-boarding Via Policy](../azure-monitor/insights/vminsights-enable-policy.md)| &#10007; | VM insights workbook  |
| DnsEvents | [Connect DNS](connect-dns.md) | &#10003; | |
| W3CIISLog | [Connect IIS logs](../azure-monitor/platform/data-sources-iis-logs.md)  | &#10007; | |
| WireData | [Connect Wire Data](../azure-monitor/insights/wire-data.md) | &#10007; | |
| WindowsFirewall | [Connect Windows Firewall](connect-windows-firewall.md) | &#10003; | |
| AADIP SecurityAlert  | [Connect Azure AD Identity Protection](connect-azure-ad-identity-protection.md)  | &#10003; | |
| AATP SecurityAlert  | [Connect Microsoft Defender for Identity](connect-azure-atp.md) (formerly Azure ATP) | &#10003; | |
| ASC SecurityAlert  | [Connect Azure Defender alerts](connect-azure-security-center.md) from Azure Security Center  | &#10003; | |
| MCAS SecurityAlert  | [Connect Microsoft Cloud App Security](connect-cloud-app-security.md)  | &#10003; | |
| SecurityAlert | | | |
| Sysmon (Event) | [Connect Sysmon](https://azure.microsoft.com/blog/detecting-in-memory-attacks-with-sysmon-and-azure-security-center)<br> [Connect Windows Events](../azure-monitor/platform/data-sources-windows-events.md) <br> [Get the Sysmon Parser](https://github.com/Azure/Azure-Sentinel/blob/master/Parsers/Sysmon/Sysmon-v10.42-Parser.txt)| &#10007; | Sysmon collection is not installed by default on virtual machines. For more information on how to install the Sysmon Agent, see [Sysmon](/sysinternals/downloads/sysmon). |
| ConfigurationData  | [Automate VM inventory](../automation/change-tracking/overview.md)| &#10007; | |
| ConfigurationChange  | [Automate VM tracking](../automation/change-tracking/overview.md) | &#10007; | |
| F5 BIG-IP | [Connect F5 BIG-IP](https://devcentral.f5.com/s/articles/Integrating-the-F5-BIGIP-with-Azure-Sentinel)  | &#10007; | |
| McasShadowItReporting  |  | &#10007; | |
| Barracuda_CL | [Connect Barracuda](connect-barracuda.md) | &#10003; | |


## Next steps

- To get started with Azure Sentinel, you need a subscription to Microsoft Azure. If you do not have a subscription, you can sign up for a [free trial](https://azure.microsoft.com/free/).
- Learn how to [onboard your data to Azure Sentinel](quickstart-onboard.md), and [get visibility into your data, and potential threats](quickstart-get-visibility.md).