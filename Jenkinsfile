pipeline {
    agent any
    parameters{
        string(name: "fName", defaultValue: "Kamal", description: "")
        choice(name: "city", choice: ['one', 'two', 'three'], description: '')
    }
    stages {
        stage("one"){
            steps {
                echo "${params.fName}"
            }
        }
    }
}
