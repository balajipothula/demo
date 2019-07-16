pipeline {

  agent {
    label("master")
  }

  stages{

    stage("Git Clone") {
      steps{
        git(credentialsId: "git", url: "https://github.com/balajipothula/results.git", branch: "master")
      }
    }

    stage("MyBatis Execution") {
      steps{
        script{
           sh '''
              export MIGRATIONS_HOME=/home/jenkins/mybatis-migrations-3.3.5
              export MIGRATIONS=/home/jenkins/mybatis-migrations-3.3.5/bin
              export PATH=$PATH:$MIGRATIONS
              migrate $command $count         
              '''
        }
      }
    }

  }

}
