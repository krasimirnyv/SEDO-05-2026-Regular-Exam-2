pipeline {
    agent any

    environment {
        PATH = "/usr/local/share/dotnet:${env.PATH}"
        DOTNET_VERSION = "6.0.x"
    }

    stages {
        stage("Checkout the repository") {
            steps {
                checkout scm
            }
        }

        stage("Restore dependencies") {
            steps {
                sh 'dotnet restore'
            }
        }

        stage("Build") {
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage("Run Unit Tests") {
            steps {
                sh 'dotnet test Homies.Tests/Homies.Tests.csproj --no-build --verbosity normal'
            }
        }

        stage("Run Integration Tests") {
            steps {
                sh 'dotnet test Homies.IntegrationTests/Homies.IntegrationTests.csproj --no-build --verbosity normal'
            }
        }
    }
}