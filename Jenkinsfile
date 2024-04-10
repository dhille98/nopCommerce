pipeline {
    agent {  label 'DOTNET'  }
    triggers {
        pollSCM ( '* * * * *')
    }
    stages {
        stage('git clone') {
            steps {
                git url: 'https://github.com/dhille98/nopCommerce.git', branch: 'dev'
            }


        }
        stage('build') {
            steps {
                //sh 'mkdir publish'
                sh 'dotnet publish -c Release src/Presentation/Nop.Web/Nop.Web.csproj -o publish'
                sh 'zip -q Nop.Web.zip pubilsh/**'
                archiveArtifacts artifacts: 'publish/'
            }
        }
    }
}