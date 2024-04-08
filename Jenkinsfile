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
                
                // sh 'dotnet publish -c Release src/Presentation/Nop.Web/Nop.Web.csproj -o ./publish'
                dotnetPublish configuration: 'Realese',
                outputDirectory : 'publish',
                project: 'src/Presentation/Nop.Web/Nop.Web.csproj'
                
            }
        }
    }
    
}