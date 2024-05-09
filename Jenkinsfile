pipeline {
    agent any

    paramaters {
        booleanParam(defaultValue: false, description: "Enable service?", name: "myBoolean")
    }
    stages {
        stage("demo"){
            steps {
                echo "booleanParam is set to: ${params.myBoolean}"
            }
        }
    }
}
