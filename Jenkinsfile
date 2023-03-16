pipeline {
    agent any
    environment {
//           IMAGE_TAG = sh(returnStdout: true, script: 'cat /mad-version/mad-backend').trim()
//           JAR_VERSION = sh(returnStdout: true, script: """
//           grep \"VERSION_NAME\" version.properties | awk -F\"=\" \'{print \$2}\'| awk -F. -v OFS=. \'NF==1{print ++\$NF}; NF>1{if(length(\$NF+1)>length(\$NF))\$(NF-1)++; \$NF=sprintf(\"%0*d\", length(\$NF), (\$NF+1)%(10^length(\$NF))); print}'
//           """).trim()
    }
    stages {
          stage('SCM') {
              steps {
                 checkout scm
              }
          }
        stage('Docker Build') {
            steps {
//                 sh "chmod +x gradlew"
//                 sh "sudo ./gradlew clean"
//                 sh "sudo ./gradlew incrementVersion"
//                 sh "sudo ./gradlew build"
//                 sh "sudo docker build --build-arg JAR_VER=$JAR_VERSION -t 43.201.29.236:5000/mad-backend:$IMAGE_TAG ."
            }
        }
        stage('Docker push') {
            steps {
                sh "sudo docker login 43.201.29.236:5000 -u admin -p mad!"
                sh "sudo docker push 43.201.29.236:5000/demo:$IMAGE_TAG"
           }
        }
        stage('Tag Version UP') {
            steps {
//                 sh "echo \$(echo ${IMAGE_TAG} | awk -F. -v OFS=. 'NF==1{print ++\$NF}; NF>1{if(length(\$NF+1)>length(\$NF))\$(NF-1)++; \$NF=sprintf(\"%0*d\", length(\$NF), (\$NF+1)%(10^length(\$NF))); print}') > /mad-version/mad-backend"
            }
        }
    }
}