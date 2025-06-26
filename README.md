## **Project Overview**

In this project, you’ll create a security infrastructure design document for **WidgetCo**, a fictional online retailer specializing in high-end, handcrafted widgets. WidgetCo has a small but growing workforce of 50 employees, and as the company handles sensitive customer information (including payment details), ensuring the security of both internal and external systems is crucial.

### **Assignment**
As the security consultant for WidgetCo, your task is to design a security infrastructure that addresses the organization’s security needs. The security services and tools you describe in the document must be able to meet the specific requirements of the organization.

The goal is to develop a detailed security plan that covers various aspects of the organization’s operations, including secure website access, network security, and remote access solutions for employees.

### **Organization Requirements**
WidgetCo requires security measures to be implemented for the following systems:

- **An external website** allowing users to browse and purchase widgets
- **An internal intranet website** for employees to use for internal communication and operations
- **Secure remote access** for engineering employees who need to access internal systems from outside the office
- **Reasonable, basic firewall rules** to protect the network
- **Wireless coverage** in the office with secure access for employees and guests
- **Reasonably secure configurations for laptops**, ensuring that sensitive data is protected, especially in case of loss or theft

Since this is a retail company that will be handling customer payment data, the organization would like to be extra cautious about privacy. They don't want customer information falling into the hands of an attacker due to malware infections or lost devices.

Additionally, engineers will require access to internal websites, along with remote, command-line access to their workstations.

---


The plan will include the following key elements:

- **Authentication system**: Design a secure authentication framework for users and employees.
- **External website security**: Implement measures to protect the external website used for customer transactions.
- **Internal website security**: Secure the intranet site used by employees for internal operations.
- **Remote access solution**: Develop a solution for secure remote access for engineering employees.
- **Firewall and basic rules recommendations**: Recommend appropriate firewall configurations to protect the organization’s network.
- **Wireless security**: Design secure wireless network access policies for both employees and guests.
- **VLAN configuration recommendations**: Recommend VLAN configurations to segment network traffic and enhance security.
- **Laptop security configuration**: Specify configurations for securing employee laptops, especially in case of loss or theft.
- **Application policy recommendations**: Create policies for secure usage of applications within the organization.
- **Security and privacy policy recommendations**: Develop a set of security and privacy guidelines to ensure the protection of sensitive data.
- **Intrusion detection or prevention**: Recommend tools or systems for detecting and preventing intrusions, particularly for systems containing customer data.

---

## **Detailed Security Plan**

### **1. Authentication System**
- Implement **Multi-Factor Authentication (MFA)** for all employee access to internal systems and remote access.
- Use **Active Directory (AD)** with **LDAP** for centralized user management and access control.
- Enforce strong **password policies** with minimum length and complexity requirements.
- Use **OAuth 2.0** / **OpenID Connect** for external website user authentication to allow secure customer login.

### **2. External Website Security**
- Use **HTTPS/TLS encryption (TLS 1.2 or higher)** for all external website traffic to protect user data in transit.
- Implement a **Web Application Firewall (WAF)** to block common attacks like SQL Injection, XSS, and DoS.
- Regularly perform **vulnerability scans** and **penetration testing** on the site.
- Limit exposure of sensitive customer data by implementing **data encryption at rest** for payment info and using **PCI DSS compliant payment gateways**.
- Implement **Content Security Policy (CSP)** and secure cookie flags (**HttpOnly**, **Secure**).

### **3. Internal Website Security**
- Restrict access to employees only, protected by **AD authentication** and **MFA**.
- Host the internal website on a **private VLAN** inaccessible from external networks.
- Use **HTTPS/TLS** internally for encrypted access.
- Regularly perform **security updates and patching** of web servers and applications.
- Enable **role-based access control (RBAC)** for sensitive intranet resources.

### **4. Remote Access Solution**
- Deploy a **VPN solution** (e.g., **OpenVPN**, **IPsec**) to allow secure encrypted remote connections for engineers.
- Require **MFA** on VPN access.
- Limit remote access only to necessary internal resources via **access control lists (ACLs)** on the VPN gateway.
- Use **host-based firewalls** and **endpoint security** on engineer workstations.

### **5. Firewall and Basic Rules Recommendations**
- Configure the **perimeter firewall** with default deny (**implicit deny**) for all inbound traffic except:
  - **HTTP/HTTPS** to external website servers.
  - **VPN ports** for remote access.
  - Necessary **outbound rules** for employee internet access.
- Block all unnecessary ports and protocols.
- Implement **stateful inspection** and logging for monitoring.

### **6. Wireless Security**
- Use **WPA3 Enterprise** for wireless encryption.
- Create separate **VLANs** for employee wireless and guest wireless access.
- Require **802.1X authentication** with **RADIUS** for employees on wireless.
- Disable **WPS**.
- Regularly change wireless access point passwords and monitor for rogue access points (**APs**).

### **7. VLAN Configuration Recommendations**
- **VLAN 10**: Employee wired network
- **VLAN 20**: Employee wireless network
- **VLAN 30**: Guest wireless network (with internet-only access)
- **VLAN 40**: Servers (external and internal websites)
- **VLAN 50**: Management (network devices, admin access)

- Enforce **inter-VLAN ACLs** to restrict access between VLANs, only allowing necessary communication.

### **8. Laptop Security Configuration**
- **Full disk encryption** (e.g., **BitLocker**, **FileVault**) to protect data if devices are lost or stolen.
- Enforce **automatic screen lock** after 5 minutes of inactivity.
- Require **strong passwords** and **MFA** where possible.
- Enable **host-based firewalls** and **endpoint antivirus/antimalware** software.
- Configure **automatic OS and software patching**.
- Disable unnecessary services and **USB ports** if possible.

### **9. Application Policy Recommendations**
- Only allow approved software installation via **application whitelisting** tools.
- Enforce **least privilege** principle on software and user accounts.
- Block unauthorized file sharing or **peer-to-peer software** to reduce malware risk.
- Implement regular audits of installed software across company devices.

### **10. Security and Privacy Policy Recommendations**
- Enforce **data privacy policies** for customer information, with training for employees on handling sensitive data.
- Require **incident reporting procedures** for suspicious activity or data breaches.
- Establish **regular security awareness training** for all employees.
- Implement **password policies**, **MFA requirements**, and **remote work security protocols**.
- Maintain **data retention** and **destruction policies** aligned with legal requirements.

### **11. Intrusion Detection or Prevention for Systems Containing Customer Data**
- Deploy a **Network Intrusion Detection System (NIDS)** to monitor traffic on **VLAN 40 (servers)**.
- Implement a **Host-based Intrusion Detection System (HIDS)** on critical servers.
- Configure **alerts** for suspicious traffic or behavior indicating potential compromise.
- Regularly review logs and update **IDS signatures**.

---

### **Conclusion**

The proposed security infrastructure design for **WidgetCo** aims to safeguard the company’s sensitive data, internal systems, and customer interactions by implementing best practices in security. By addressing key areas such as authentication, external and internal website security, remote access, network segmentation, and endpoint protection, WidgetCo will significantly reduce its exposure to security threats.

With a strong emphasis on protecting customer data—especially payment information—through encryption, secure access, and continuous monitoring, this plan ensures that WidgetCo meets industry standards such as **PCI DSS** and aligns with organizational privacy and compliance requirements.

Furthermore, the adoption of Multi-Factor Authentication (MFA), regular patching, network segmentation with VLANs, and intrusion detection systems will enhance the overall resilience of the organization’s infrastructure against potential breaches or unauthorized access.

By implementing these security measures, WidgetCo will be able to foster a secure and trusted environment for both its employees and customers, while minimizing the risk of data breaches, malware infections, and system compromises. Regular updates, audits, and security awareness training will ensure that the company remains proactive in its security posture as it grows.

---

### **Acknowledgements**

This security infrastructure design project was completed as part of the **Google IT Support Professional Certificate** course on **Coursera**. The course provided valuable foundational knowledge in IT support, security, and system administration, which was applied to design a robust and secure infrastructure for **WidgetCo**, a fictional organization. 

The course helped develop essential skills in areas such as:
- System administration
- Security best practices
- Network management
- Troubleshooting

For more information about the Google IT Support Professional Certificate, please visit [Coursera](https://www.coursera.org/professional-certificates/google-it-support).
