# <ins>Capstone Project - Automating Deployement of an E-commerce Website</ins>

## <ins>Project Scenario</ins>
  A technology consulting firm, is adopting a cloud architecture for its software applications. As a DevOps Engineer, your task is to design and implement a robust CI/CD pipeline using Jenkinsto automate the deploymentof a web application. The goal is to achieve continuous integration, continuous deployment, and ensure the scalability and reliability of the applications.

## <ins>Project Components</ins>

###  1.) <ins>Jenkins Server Setup</ins>

  **Objective:** Configure Jenkins server for CI/CD pipleine automation.

  **Steps:**

  - Install Jenkins on a dedicated server.

    - Firstly, I update the server with the following command line

          sudo apt update

    - Then, I install Java before installing Jenkins

          sudo apt install default-jre
    ![Screenshot (297)](https://github.com/user-attachments/assets/1bf7779c-78cb-4ab0-a896-1735ad66ee95)
    ![Screenshot (280)](https://github.com/user-attachments/assets/94abb8da-fa97-4761-a8e2-ca893401e684)

    - Then, we confirm that Java is running on the server
   
          java -version
    ![Screenshot (281)](https://github.com/user-attachments/assets/2738ad14-8b2d-4684-824d-e7d53d71f612)

  - Installing Jenkins

      - Firstly, i added the GPG Key

            sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
    ![Screenshot (282)](https://github.com/user-attachments/assets/910c1d39-d959-4691-b4cf-400e902ccbdc)

      - Secondly, I added the Jenkins Repository

            echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
    ![Screenshot (283)](https://github.com/user-attachments/assets/67d54434-4232-40b4-a3c2-ba78a5ff0d64)

      - Thirdly, I load the latest packages

            sudo apt update
    ![Screenshot (284)](https://github.com/user-attachments/assets/47b048ff-f727-4027-a6db-c1f0c614a907)

      - Finally, I install Jenkins in the server

            sudo apt install jenkins
    ![Screenshot (286)](https://github.com/user-attachments/assets/eb02cc35-7f62-4950-9180-c9d241045507)

      - I check to confirm that Jenkins is running on the server

            jenkins --version
    ![Screenshot (287)](https://github.com/user-attachments/assets/6184849e-361e-4a5b-adbb-8c9b1f2d63ad)

  - Set up necessary plugins (Git, Docker, etc.)

      - I create new inbound rules for port 8080 in security group for the Jenkins Server

    ![Screenshot (287)](https://github.com/user-attachments/assets/99cfcbfd-c944-4e17-9471-12a6af60a7ba)

      - I opened my jenkins instance IP address on my web browser with port 8080
    
    ![Screenshot (289)](https://github.com/user-attachments/assets/ec6f72da-c16c-4022-811b-070601b09b8e)

      - On my Jenkins instance, i used the following command line to know my password

            sudo cat /var/lib/jenkins/secrets/initialAdminPassword 
    ![Screenshot (290)](https://github.com/user-attachments/assets/0425d579-0390-4402-a166-5b90be556450)
    ![Screenshot (291)](https://github.com/user-attachments/assets/68445921-b353-4ac5-ab5c-53b39f884727)

      - Install the plugins

    ![Screenshot (292)](https://github.com/user-attachments/assets/2523b1f7-b052-4621-937f-54fbcbad2857)
    ![Screenshot (293)](https://github.com/user-attachments/assets/122a5b36-dfe3-426f-b39a-0109e7a37745)

  - Configure Jenkins with required security measures.

      - I created a new username and password which i will use to log in to the jenkins instance

    ![Screenshot (294)](https://github.com/user-attachments/assets/05dd06cb-9523-4fd0-9df0-0c82a57c9244)
    ![Screenshot (295)](https://github.com/user-attachments/assets/dc4a95bc-586b-4dd4-ae8d-e96ac94de395)

      - The Jenkins Instance setup has now been completed

    ![Screenshot (296)](https://github.com/user-attachments/assets/cf2c2204-852d-496d-950d-9748f405f4f4)


### 2.) <ins>Source Code Management Repository Integration</ins>

  **Objective:** Connect Jenkins to the version control system for source code management.

  **Steps:**

  - Integrate Jenkins with the source code management repository (e.g. GitHub, Bitbucket).

      - Firstly, I created a GitHub repository called "Jenkins-Server" and copy the repository URL

    ![Screenshot (303)](https://github.com/user-attachments/assets/c906ff42-4ffc-4cac-9185-26453524bf3a)

      - then, I enter the repository URL into the source code management section of the Jenkins configuration

    ![Screenshot (304)](https://github.com/user-attachments/assets/75e3d308-98bb-4bb9-8b12-5ec89d704d72)
    ![Screenshot (305)](https://github.com/user-attachments/assets/c0aab28f-b8fa-44f8-b47a-b80c4762689a)

  - Configure webhooks for automatic triggering of Jenkins builds.

      - On the Github page of "Jenkins-Server", i clicked on the settings tab and navigated down to the webhooks section. I input the IP address and Port number for the Jenkins Instance and select "application/json" as the content type.

    ![Screenshot (307)](https://github.com/user-attachments/assets/7deb3cae-2d69-48e2-9511-b22f101790a7)

### 3.) <ins>Jenkins Freestyle Jobs for Build and Unit Tests</ins>

  **Objective:** Create Jenkins Freestyle jobs for building a web application and running unit tests.

  **Steps:**

  - Set up a Freestyle job for building the application.

      - From the Jenkins Dashboard on the left side, i clicked on "new item". I named it "First Jenkins Job" and selected Freestyle project.

    ![Screenshot (300)](https://github.com/user-attachments/assets/4bd23beb-408b-4a7d-9292-cb4a941ea25f)

### 4.) <ins>Jenkins Pipeline for Web Application</ins>

  **Objective:** Develop a Jenkins Pipeline for running a web application.

  **Steps:** 
  
  - Create a Jenkins Pipeline script to run a web application.

    <ins>Creating the Pipeline</ins>

      - From the Jenkins Deashboard menu on the left side, I clicked on "new item".

    ![Screenshot (309)](https://github.com/user-attachments/assets/0baeeac3-1afb-486d-a764-36e9e750de15)

      - Then i named the new item, "First Jenkins Pipeline" and selected the pipeline option to create a pipeline.

    ![Screenshot (310)](https://github.com/user-attachments/assets/aa5fda87-5d54-4608-bba5-db25549da978)

      - Then, as i did previously with the freestyle job, i configured the pipeline with the same Github hook build trigger

    ![Screenshot (311)](https://github.com/user-attachments/assets/b3874020-61d1-4145-a720-28d8d929586c)

    <ins>Writing Jenkins Pipeline Script</ins>

      - I entered this pipeline script into the pipeline configuration.

                          pipeline \{
                      agent any
                  
                      stages \{
                          stage('Connect To Github') \{
                              steps \{
                                      checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/OlisehKN/Jenkins-Server.git']])
                              \}
                          \}
                          stage('Build Docker Image') \{
                              steps \{
                                  script \{
                                      sh 'docker build -t dockerfile .'
                                  \}
                              \}
                          \}
                          stage('Run Docker Container') \{
                              steps \{
                                  script \{
                                      sh 'docker run -itd -p 8081:80 dockerfile'
                                  \}
                              \}
                          \}
                      \}
                  \}

     - Next, i click on the "pipeline syntax" button below the script and search for and select "Checkout: check out from version control"

    ![Screenshot (312)](https://github.com/user-attachments/assets/3c123f5c-fbfa-49a9-bbaf-0f8bfb52d8e7)

    ![Screenshot (313)](https://github.com/user-attachments/assets/5fbf1d4e-ae7e-43fd-940a-bc62929e07bf)

     - I add my Github repository URL and make sure that the "main" branch is selected.

    ![Screenshot (317)](https://github.com/user-attachments/assets/82b22549-daad-4e09-99e4-00e589507c93)

     - Then generate the pipeline script

    ![Screenshot (318)](https://github.com/user-attachments/assets/aa19d8d2-2270-4737-83e5-7194ab0d6a8d)

     - Lastly, i replace the former script under the "Connect Github" stage, with the newly generated script.
   
    ![Screenshot (319)](https://github.com/user-attachments/assets/1a9ebab8-adf6-4e5f-a569-59e38902379b)

    ![Screenshot (320)](https://github.com/user-attachments/assets/b7ec6500-0e07-4680-888b-c5b43a2299bd)

