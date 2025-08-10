# Stealth-Route-Lab
AWS EC2 lab setup for secure, anonymized browsing and reconnaissance using proxychains and Tor.
## **Overview**
- Deploy an EC2 instance running Ubuntu.
- Install and configure **Tor** and **Proxychains**.
- Route selected network traffic through Tor.
- Test using network tools such as `curl`, `wget`, and `nmap`.
## **Objective**
The goal of this lab is to:
1. Anonymize outbound connections from an EC2 instance.
2. Validate traffic routing via Tor.
3. Use Proxychains to tunnel specific tool traffic through Tor.
## **Installation**
***SSH into the Instance***
```bash
ssh -i "key-pair.pem" ubuntu@<EC2-Public-IP>
sudo apt update
sudo apt install tor wget proxychains4 -y
```
### **Configuration**
***Edit proxychains configuration***
```bash
sudo nano /etc/proxychains.conf
```
***uncomment***
```bash
dynamic_chain
```
***proxylists***
```bash
socks5 127.0.0.1 9050
http   127.0.0.1 8080
```
## **Testing**
***Start Tor, confirm EC2's public IP and Tor exit node IP***
```bash
sudo systemctl start tor
curl ifconfig.me
proxychains curl ifconfig.me
```
## **Conclusion**
This lab demonstrated how to route EC2 traffic through Tor with Proxychains, achieving anonymized and secure outbound connections. It provides a foundation for privacy-focused browsing and reconnaissance.
