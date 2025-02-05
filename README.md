# <ins>Capstone Project - Automating Deployement of an E-commerce Website</ins>

## <ins>Project Scenario</ins>
  A technology consulting firm, is adopting a cloud architecture for its software applications. As a DevOps Engineer, your task is to design and implement a robust CI/CD pipeline using Jenkinsto automate the deploymentof a web application. The goal is to achieve continuous integration, continuous deployment, and ensure the scalability and reliability of the applications.

## <ins>Project Components</ins>

###  1.) <ins>Jenkins Server Setup<?ins>

  **Objective:** Configure Jenkins server for CI/CD pipleine automation.

  **Steps:**

  - Install Jenkins on a dedicated server.

    - Firstly, I update the server with the following command line

          sudo apt update

    - Then, I install Java before installing Jenkins

          sudo apt install default-jre


    - Then, we confirm that Java is running on the server
   
          java -version

  - Installing Jenkins

      - Firstly, i added the GPG Key

            sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

      - Secondly, I added the Jenkins Repository

            echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

      - Thirdly, I load the latest packages

            sudo apt update

      - Finally, I install Jenkins in the server

            sudo apt install jenkins

      - I check to confirm that Jenkins is running on the server

            jenkins --version

  - Set up necessary plugins (Git, Docker, etc.)

      - I create new inbound rules for port 8080 in security group for the Jenkins Server

      - I opened my jenkins instance IP address on my web browser with port 8080
   
      - On my Jenkins instance, i used the following command line to know my password
   
            sudo cat /var/lib/jenkins/secrets/initialAdminPassword 
    
      - Install the plugins

  - Configure Jenkins with required security measures.

      - I created a new username and password which i will use to log in to the jenkins instance
   
        
