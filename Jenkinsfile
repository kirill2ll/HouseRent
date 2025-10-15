pipeline {
    agent any
    environment {
        DOTNET_ROOT = "/usr/share/dotnet"
        PATH = "/usr/share/dotnet:$PATH"
    }
    stages {
        stage('Restore dependencies') { steps { sh 'dotnet restore' } }
        stage('Build') { steps { sh 'dotnet build --no-restore' } }
        stage('Test') { steps { sh 'dotnet test --no-build --verbosity normal' } }
    }
}
