pipeline{
agent any
tools {
    maven 'mymaven'
}
stages {
    stage('clone repo') {
        steps {            git branch: 'main', url: 'https://github.com/shubhamgunjal198/DevOpsClassCodes.git'
            // Add your build commands here
        }
    }
    stage('Compile') {
        steps {
            sh 'mvn compile'
            // Add your test commands here
        }
    }
    stage('code review') {
        steps {
            sh 'mvn pmd:pmd'
            // Add your deployment commands here
        }
        post {
            success { 
                recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [pmdParser(pattern: '**/pmd.xml')]
            }
        }
    }
    stage('test code') {
        steps {
            sh 'mvn test'
        }
        post {
            success {
             junit 'target/surefire/*.xml'
            }
        }   
    }
    stage('package code') {
        steps {
            sh 'mvn package'
        }
    }

}
}
