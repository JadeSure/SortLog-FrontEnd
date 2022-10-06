pipeline {
     agent any
     
        //Install denpendencies 
    stages{
        stage('Install dependency')
        {
            steps{
             sh 'ls'
             sh 'pwd'
             echo "Installing packages"
             sh 'yarn install'
             }          
        }

        stage('yarn build') 
        {
            steps{
             sh "yarn export "
             sh 'ls -la ./out'
             }
        } 
    }
}