#STEP-1: Update system
sudo yum update -y

#STEP-2: Install Java 17 (required for SonarQube server)
sudo yum install java-17-amazon-corretto -y

#STEP-3: Install wget and unzip
sudo yum install wget unzip -y

#STEP-4: Download SonarQube
cd /opt
sudo wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.5.1.90531.zip

#STEP-5: Unzip SonarQube
sudo unzip sonarqube-10.5.1.90531.zip

#STEP-6: Rename directory
sudo mv sonarqube-10.5.1.90531 sonarqube

#STEP-7: Create sonar user
sudo useradd sonar

#STEP-8: Change ownership
sudo chown -R sonar:sonar /opt/sonarqube

#STEP-9: Start SonarQube
cd /opt/sonarqube/bin/linux-x86-64

sudo -u sonar ./sonar.sh start
