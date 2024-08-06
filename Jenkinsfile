#def gv

pipeline {
    agent any
    stages {
        #stage("init") {
            #steps {
                #script {
                    #gv = load "script.groovy"
                #}
            #}
        #}
        stage("build jar") {
            when {
                expression {
                   Branch_Name == 'main'
                }
            }
            steps {
                script {
                    echo "building jar"
                    //gv.buildJar()
                }
            }
        }
        stage("build image") {
            when {
                expression {
                    Branch_Name == 'main'
            }
            steps {
                script {
                    echo "building image"
                    //gv.buildImage()
                }
            }
        }
        stage("deploy") {
            when {
                expression {
                    Branch_Name == 'main'
            }
            steps {
                script {
                    echo "deploying"
                    //gv.deployApp()
                }
            }
        }
    }   
}
