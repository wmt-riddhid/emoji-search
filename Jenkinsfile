pipeline{
    agent{
        docker{
            image 'node:16.14.2'
        }
    }
    environment{
        NETLIFY_AUTH_TOKEN = credentials('NETLIFY_AUTH_TOKEN_R')
        NETLIFY_SITE_ID = credentials('NETLIFY_SITE_ID_R')

    }
    stages{
        stage('Build'){
            steps{
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Deliver'){
            steps{
                sh 'npm install netlify-cli'
                sh 'npx netlify deploy --site $NETLIFY_SITE_ID --auth $NETLIFY_AUTH_TOKEN --dir build/ --prod'
            }
        }
    }
}