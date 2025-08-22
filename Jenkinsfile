
pipeline{
    agent {
        label 'linux_node'
    }
    tools{
        maven'mymaven'
    }
    stages{
        stage{
        steps('git clone repo'){
            git branch:'Master', url:'https://github.com/shubhamgunjal198/DevOpsClassCodes.git'
        }
        }
        stage('code compile'){
            steps{
            sh'mvn compile'
        }
        }
        stage('code review'){
            steps{
                sh 'pmd:pmd'
            }
            post{
                success{
                    recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [pmdParser(pattern: '**/pmd.xml')]
                }
            }
        }
        stage('test code'){
            steps{
                sh 'mvn test'
            }
            post{
                success{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('package code'){
            steps{
                sh 'mvn package'
            }
        }

    }
    
    
}
