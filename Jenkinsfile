pipeline{
    agent any
    stages{
        stage("testing"){
            steps{
                git 'https://github.com/batpool/nginx-google-pagespeed'
            }
            
            post{
                success{
                    echo "hi dude"
                }
            }
        }
        
        stage("prod"){
            steps{
                git 'https://github.com/batpool/nginx-google-pagespeed'
            }
            
            post{
                success{
                    echo "pushed to production"
                }
            }
        }
    }
}
