pipeline {
    agent any

    stages {
        stage('Install .NET SDK') {
            steps {
                sh '''
                wget https://dot.net/v1/dotnet-install.sh -O dotnet-install.sh
                chmod +x dotnet-install.sh
                ./dotnet-install.sh --channel 6.0
                '''
                sh 'export PATH=$PATH:$HOME/.dotnet'
            }
        }

        stage('Restore dependencies') {
            steps {
                sh '~/.dotnet/dotnet restore'
            }
        }

        stage('Build') {
            steps {
                sh '~/.dotnet/dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                sh '~/.dotnet/dotnet test --no-build --verbosity normal'
            }
        }
    }
}
