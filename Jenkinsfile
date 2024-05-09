pipeline {
    agent any
    parameters{
        string(name: "fName", defaultValue: "Kamal", description: "")
    }
    stages {
        stage("one"){
            steps {
                echo '${params.fName}'
            }
        }
    }
}
