pipeline {
    agent { label 'DOTNET'}

    stages {
        stage('git') {
            steps{
                git url: 'https://github.com/dhille98/nopCommerce.git',
                    branch: 'dev'

            }
            
        }
        stage('build'){
            steps{
                sh 'mkdir ~/publish'
                sh 'dotnet publish -c Release src/Presentation/Nop.Web/Nop.Web.csproj -o ./publish'
                sh 'zip -r Nop.Web.zip publish'
            }
        }
    }
    
}