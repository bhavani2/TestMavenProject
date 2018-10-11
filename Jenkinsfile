pipeline {
    
    agent any 
    
    parameters {
        
        string(name: 'BRANCH', defaultValue: 'master', description: 'Please Provide Branch Name')
        
    }
    
    stages {
        
        stage ('Source Code Checkout') {
            
            when {
                
                expression { params.BRANCH == 'master' }
                
            }
            
            steps {
                
                checkout([$class: 'GitSCM', branches: [[name: '*/${BRANCH}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'BhavaniGITHub', url: 'https://github.com/bhavani2/TestMavenProject.git']]])

            }
            
        }
        
        stage ('Build') {
            steps {
               
               //echo "Provided Branch name is ${params.BRANCH}" 
               sh 'echo $BRANCH'
               sh 'mvn clean install'
                
            }   
        
        }
        
        stage ('Archive Artifacts') {
            
            steps {
            
                archiveArtifacts '**/*.jar'
            }
        }
    }
}