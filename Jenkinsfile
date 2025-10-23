pipeline{
    agent any

    stages{
        stage("Restore the dependencies"){
            when{ 
                branch pattern: "(main|feature/.*)", comparator: "REGEXP"
            }
            steps{
                bat 'dotnet restore'
            }
        }
        stage("Build the application"){
            steps{
                bat 'dotnet build --no-restore'
            }
        }
        stage("Run the unit and integration tests"){
            when{ 
                branch pattern: "(main|feature/.*)", comparator: "REGEXP"
            }
            steps{
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
