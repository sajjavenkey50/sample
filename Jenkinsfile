pipeline {
    agent any 

    stages {
        stage('Get Latest Sourcecode') {
            steps {
                git 'https://github.com/sajjavenkey50/sample.git'
            }
        }
        stage('Function to conversion of excel sheet into Data frame') {
            steps {
                sh "python3 parametercoverage1.py"
            }
        }
        stage('Read the xml and convert to data frame') {
            steps {
                sh "python3 parametercoverage2.py" 
            }
        }
        stage('Function to find the Parameter in the xml data frame') {
            steps {
                sh "python3 parametercoverage3.py"
            }
        }
        stage('Function to pass or fail the build depending on the previous step') {
            steps {
                sh "python3 parametercoverage4.py" 
            }
        }
        
     post {
            success {
                mail (to: 'sajja.venkat05@gmail.com',
         subject: "Job '${env.JOB_NAME}'- (${env.BUILD_NUMBER}) has SUCCEED",
         body: "Please go to ${env.BUILD_URL} for more details. ");
            }
            failure {
                mail (to: 'sajja.venkat05@gmail.com',
         subject: "Job '${env.JOB_NAME}'- (${env.BUILD_NUMBER}) has FAILED",
         body: "Please go to ${env.BUILD_URL} for more details. ");
            }
        }
        
        
        stage('Function to develop a report and send an email') {
            steps {
                sh "python3 parametercoverage5.py" 
            }
        }
        stage('Function to convert dev.txt to data frame') {
            steps {
                sh "python3 parametercoverage6.py"
            }
        }
        stage('Function to find the average of parameters') {
            steps {
                sh "python3 parametercoverage7.py"
            }
        }
    }
}
