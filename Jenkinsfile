pipeline {
     agent any
     
        //Install denpendencies 
    stages{
        stage('Install dependency')
        {
            steps{
             echo "Installing packages"
             sh 'yarn install'
             }          
        }

        stage('yarn build') 
        {
            steps{
             sh "yarn next build && yarn next export "
             sh 'ls -la ./out'
             }
        } 
    }
}