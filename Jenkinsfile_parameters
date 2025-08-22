pipeline{

tools{
  maven 'mymaven'
}

agent any 

parameters{
    choice(name: 'ENV', choices: ["","Dev","QA"])
}

stages{

stage('Build on Dev ENV'){
  when{  // when should this stage steps be exeucted 
     expression{params.ENV == "Dev"}   // expression = condition
  }
steps{
   git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
   sh 'mvn package'
}

}

stage('Test on QA ENV'){

when{
   expression{params.ENV == "QA"}   // expression = condition
}

 
steps{
   git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
   sh 'mvn test'
}

}

}

}
