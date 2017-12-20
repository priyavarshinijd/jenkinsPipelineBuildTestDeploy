node('master') {
  
  stage ('Git Checkout'){
     git 'https://github.com/priyavarshinijd/spring-petclinic.git'
     echo 'checkout done'
}

checkout([$class: 'GitSCM', branches: [[name: '*/master']], browser: [$class: 'GithubWeb', repoUrl: 'https://github.com/priyavarshinijd/'], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/priyavarshinijd/spring-petclinic.git']]])

bat 'mvnw.cmd clean install'

bat '''cd docker
cd internal-db
docker-build -t spring-petclinic .'''
  
  
   stage('Maven Build'){
      echo 'Maven Project Compile'
      maven 'clean install'
      junit 'target/surefire-reports/**/*.xml' 
 }


   stage 'Deploy'
        echo 'Deploying Docker Image'

   stage 'Testing'
        echo 'Reporting Getting Creating'

   stage 'Job Status Status'
        echo 'Notification Sending'
}
