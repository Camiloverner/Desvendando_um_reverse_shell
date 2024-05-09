pipeline {
    agent any
    paramaters{
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
