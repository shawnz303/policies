# 1. Introduction

Iono Health, LLC ("Iono Health") is committed to ensuring the confidentiality, privacy, integrity, and availability of all electronic protected health information (ePHI) it receives, maintains, processes and/or transmits on behalf of its Customers. The following documents address core policies used by Iono Health to maintain compliance and assure the proper protections of infrastructure used to store, process, and transmit ePHI for Iono Health Customers.

Iono Health provides secure and compliant cloud-based software. This hosted software is a **Platform Add-ons** to Healthcare Blocks, our provider platform.

## 1.1 Platform Add-ons

Add-ons are compliant API-driven services that are offered as part of the Iono Health Platform. With Add-ons, Iono Health has access to data models and manages all application level configurations and security.

In the future there may be 3rd party Add-on services available as part of the Iono Health Platform. These 3rd party, or Partner, Services will be fully reviewed by Iono Health to assure they do not have a negative impact on Iono Health's information security and compliance posture.

## 1.2 Compliance Inheritance

Iono Health provides compliant hosted software infrastructure for its Customers.

Iono Health signs business associate agreements (BAAs) with its Customers. These BAAs outline Iono Health obligations and Customer obligations, as well as liability in the case of a breach. In providing infrastructure and managing security configurations that are a part of the technology requirements that exist in HIPAA and HITRUST, as well as future compliance frameworks, Iono Health manages various aspects of compliance for Customers. The aspects of compliance that Iono Health manages for Customers are inherited by Customers, and Iono Health assumes the risk associated with those aspects of compliance. In doing so, Iono Health helps Customers achieve and maintain compliance, as well as mitigates Customers risk.

Iono Health does not act as a covered entity. When Iono Healthdoes operate as a business associate (not a subcontractor), Iono Health does not interface with users to obtain or provide access to ePHI. Access to ePHI is through our customers' applications.

Certain aspects of compliance cannot be inherited. Because of this, Iono Health Customers, in order to achieve full compliance or HITRUST Certification, must implement certain organizational policies. These policies and aspects of compliance fall outside of the services and obligations of Iono Health.

Mappings of HIPAA Rules to Iono Health controls and a mapping of what Rules are inherited by Customersare covered in [§2](#2.-hipaa-inheritance).

## 1.3 Iono Health Organizational Concepts

The physical infrastructure environment is hosted at [Amazon Web Services](https://aws.amazon.com/) (AWS). The network components and supporting network infrastructure are contained within the AWS infrastructures and managed by AWS. Iono Health does not have physical access into the network components. The Iono Health environment consists of [Healthcare Blocks] (https://www.healthcareblocks.com) (HCB); nginx web servers;  Python application server, and PostgreSQL database servers; Linux Ubuntu monitoring servers; Windows Server virtual machines; OSSEC IDS services; Docker containers; and developer tool servers running on Linux Ubuntu.

Within the Iono Health Platform on AWS and HCB, all data transmission is encrypted and all hard drives are encrypted so data at rest is also encrypted; this applies to all servers - those hosting Docker containers, databases, APIs, log servers, etc. Iono Health assumes all data *may* contain ePHI, even though our Risk Assessment does not indicate this is the case, and provides appropriate protections based on that assumption.

The data and network segmentation mechanism differs depending on the primitives offered by the underlying cloud provider infrastructure:

* Within AWS, hosted load balancers segment data across dedicated Virtual Private Clouds for PaaS Customers and for Platform Add-ons.

The result of segmentation strategies employed by Iono Health effectively create RFC 1918, or dedicated, private segmented and separated networks and IP spaces, for each PaaS Customer and for Platform Add-ons.

Additionally, IPtables is used on each each server for logical segmentation. IPtables is configured to restrict access to only justified ports and protocols. Iono Health has implemented strict logical access controls so that only authorized personnel are given access to the internal management servers. The environment is configured so that data is transmitted from the load balancers to the application servers over an TLS encrypted session.

In the case of Platform Add-ons, once the data is received from the application server, a series of Application Programming Interface (API) calls is made to the database servers where the ePHI resides. The ePHI is separated into PostgreSQL and Percona databases through programming logic built, so that access to one database server will not present you with the full ePHI spectrum.

The VPN server, nginx web server, and application servers are externally facing and accessible via the Internet. The database servers, where the ePHI resides, are located on the internal Iono Health network and can only be accessed through a bastion host over a VPN connection. Access to the internal database is restricted to a limited number of personnel and strictly controlled to only those personnel with a business-justified reason. Remote access to internal servers is not accessible except through load balancers.

All Platform Add-ons and operating systems are tested end-to-end for usability, security, and impact prior to deployment to production.

## 1.4 Requesting Audit and Compliance Reports

Iono Health, at its sole discretion, shares audit reports, including its HITRUST reports and Corrective Action Plans (CAPs), with customers on a case by case basis. All audit reports are shared under explicit NDA in Iono Health format between Iono Health and party to receive materials. Audit reports can be requested by Iono Health workforce members for Customers or directly by Iono Health Customers.

The following process is used to request audit reports:

1. Email is sent to compliance-reports@ionohealth.com. In the email, please specify the type of report being requested and any required timelines for the report.
2. Iono Health staff will log an Issue with the details of the request into the Iono Health Compliance Review Activities Project on JIRA. JIRA is used to track requests status and outcomes.
3. Iono Health will confirm if a current NDA is in place with the party requesting the audit report. If there is no NDA in place, Iono Health will send one for execution.
4. Once it has been confirmed that an NDA is executed, Iono Health staff will move the JIRA Issue to "Under Review".
5. The Iono Health Security Officer or Privacy Officer must Approve or Reject the Issue. If the Issue is rejected, Iono Health will notify the requesting party that we cannot share the requested report.
4. If the Issue has been Approved, Iono Health will send the customer the requested audit report and complete the JIRA Issue for the request.

## 1.5 Version Control

Refer to the GitHub repository at [https://github.com/shawnz303/policies/](https://github.com/shawnz303/policies/) for the full version history of these policies.
