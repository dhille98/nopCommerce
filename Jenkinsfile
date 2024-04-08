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
        stage('build') {
            steps {
                //sh 'dotnet publish -o published/ -c Release src/Presentation/Nop.Web/Nop.Web.csproj'
                dotnetPublish configuration: 'Release',
                    outputDirectory: 'published',
                    project: 'src/Presentation/Nop.Web/Nop.Web.csproj'

            }
            post {
                success {
                      zip zipFile: 'nop.web.zip',
                      archive: true,
                      dir: './published',
                      overwrite: true,
                      archiveArtifacts artifacts: 'published/**',
                      onlyIfSuccessful: true
                }
            }
        }

    }
    
}