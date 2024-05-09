pipeline {
    agent any
    parameters{
        string(name: "fName", defaultValue: "Kamal", description: "")  ///PARAMETRO DE STRING
        choice(name: "city", choices: ['one', 'two', 'three'], description: '')   ///PARAMETRO DE ESCOLHA
    }
    stages {
        stage("one"){
            steps {
                echo "${params.fName}"
            }
        }
    }
}
