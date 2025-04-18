# Run a Simple Java Maven Build Job in Jenkins

## 🚀 Objective

Use Jenkins to build a simple Java application using Maven. This is your first step into CI/CD.

## 🛠 Tools Used
- AWS EC2 Ubuntu Server
- Jenkins (Installed directly on Ubuntu)
- Java JDK 8
- Maven 3.8.6
- Git

- ## 📂 Project Structure

- hello-java-maven/
- ├── pom.xml
-  └── src/

-  └── main/  
-   └── java/
-    └── HelloWorld.java

  # ⚙️ Jenkins Installation on EC2 (Ubuntu)
  
  1. Update & Install Dependencies (Use this commands)
     sudo apt update
     sudo apt install -y openjdk-8-jdk maven git wget gnupg2

  **2. Install Jenkins**
 
 wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install -y jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins

**3. Allow Jenkins Port (8080)**

Open your EC2 Security Group settings and allow inbound traffic for port 80 to 10000 (or at least port 8080).

4. Access Jenkins
Open a browser and go to:

http://<your-ec2-public-ip>:8080

**Unlock Jenkins using the password:**

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Install suggested plugins and set up your admin user.

# 🔧 Jenkins Job Configuration

Global Tool Configuration:

Go to: 
1.Manage Jenkins 
2. Global Tool Configuration

Add JDK  
JDK 8

**Add Maven**

Maven 3.8.6 (auto-install or specify path)

**Create Freestyle Project:**
New Item → hello-java-maven → Freestyle Project

Source Code Management: Choose Github 

**Build Section:**

Add Build Step :

Invoke top-level-Maven targets

Goals: clean package

Save and click Build Now

# 🔐 EC2 Security Group Setup

Make sure your EC2 Security Group has the following inbound rule:

Type: Custom TCP

Protocol: TCP

Port Range: 80-10000

Source: 0.0.0.0/0 (or your IP for security)

# ✅ Final Checklist
1. Java HelloWorld app created

2.pom.xml file ready

3.Jenkins installed and running on EC2

4.Maven installed

5.Jenkins Freestyle job created

6.Console output shows BUILD SUCCESS

7.Screenshot taken of successful build








