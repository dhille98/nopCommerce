pipeline {
    agent { label 'DOTNET'}

    triggers {
        pollSCM ('* * * * *')
    }

    stages {
        stage('git') {
            steps{
                git url: 'https://github.com/dhille98/nopCommerce.git',
                    branch: 'dev'

            }

        }
        stage('build'){
            steps{
                
                // sh 'dotnet publish -c Release src/Presentation/Nop.Web/Nop.Web.csproj -o ./publish'
                dotnetPublish configuration: 'Realese',
                outputDirectory : 'publish',
                project: 'src/Presentation/Nop.Web/Nop.Web.csproj'
                
            }
        }
        stage('zip') {
            post {
            success{
                zip zipfile: 'Nop.Web.zip',
                archive: true,
                dir: './publish',
                overwrite: true
                
            }

            
        }
        }
    }
    
}