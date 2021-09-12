pipeline {
   agent any

   tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "MAVEN_HOME"
   }

   stages {
      stage('Build') {
         steps {
            // Get some code from a GitHub repository
            sh "mvn clean compile"
         }
         }
      stage("Test") {
          steps {
             sh "mvn clean test"
                      }

      }
      stage("Deploy") {
          steps {
            git 'https://github.com/jglick/simple-maven-project-with-tests.git'
            sh "mvn -Dmaven.test.failure.ignore=true clean install"
            sh 'cp target/*.jar /home/ashelke/tomcat9/webapps/.'
            
          }

      }

      }
   }

