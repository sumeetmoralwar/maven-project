pipeline {
    agent any


    stages{
        stage('SCM Checkout'){
          git 'https://github.com/sumeetmoralwar/maven-project.git'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn install'
                }
            }
        }
        
        stage ('deploy to tomcat server') {
            steps {
                sshagent(['c1838d81-ec13-4669-acbc-9b882b3a220c']) {
                    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@13.126.47.203:/var/lib/tomcat/webapps' 
                }
            }
        }
         
}
}
