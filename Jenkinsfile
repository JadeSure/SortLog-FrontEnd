pipeline {
    agent {
        docker {
            image 'node:16-alpine'
        }
    }

    environment{
        AWS_CRED        = 'AWS_sortlog' //Change to yours //IAM role in the EC2 server instance profile admin acess.//Cloud front invalidate S3 (AWS CLI)
        AWS_REGION      = 'ap-southeast-2'// AWS region //check202210 check
    }
        
    stages{

        // stage('Install dependency')
        // {
        //     steps{
        //      echo "Installing packages"
        //      sh 'yarn install --force'
        //      }          
        // }

        // stage('yarn build') 
        // {
        //     steps{
        //      sh "yarn export "
        //      sh 'ls -la ./out'
        //      }
        // } 

        stage('upload frontend to  S3 bucket') {
            when { anyOf { branch 'master'; branch 'dev' } }
            steps {
                withAWS(credentials: AWS_CRED, region: AWS_REGION){ 
                
                    echo "deploying to S3 "
                    sh '''
                        yarn install --force
                        yarn export
                        aws s3 sync --delete ./out s3://oldiron666.sortlog
                    
                    '''
                        // aws cloudfront create-invalidation --distribution-id $BLOG_CLOUDFRONT_DISTRIBUTION_ID --paths '/*'
                }
             
            }
         
        }

    }
}
