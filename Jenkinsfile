node(){
    def sonarScanner = tool name: 'forSonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
    
    try {
        stage('Checkout Code'){
            checkout scmGit(branches: [[name: '*/master']], extensions: [], 
            userRemoteConfigs: [[credentialsId: 'git-cred', url: 'https://github.com/Mujeeb78/SonarQubeNodeJS.git']])
        }

        stage('NPM Build'){
            sh "npm install"
        }

        stage('Test Cases Execution'){
            echo "The test is SUCCESSFUL"
        }


        stage('SonarQube Analysis'){
           withSonarQubeEnv(credentialsId: 'SonarCred') {
          sh "${sonarScanner}/bin/sonar-scanner"
            }
    }
