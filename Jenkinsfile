pipeline {
    agent any
    
    tools {
        // Assurez-vous que Maven est configuré dans Jenkins sous le nom "Maven"
        // Si vous n'êtes pas sûre, supprimez ces 3 lignes 'tools' et 'maven'
        maven 'Maven' 
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Commande pour compiler (sur Windows c'est souvent mvn.cmd)
                script {
                    if (isUnix()) {
                        sh 'mvn -B -DskipTests clean package'
                    } else {
                        bat 'mvn -B -DskipTests clean package'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                script {
                    if (isUnix()) {
                        sh 'mvn test'
                    } else {
                        bat 'mvn test'
                    }
                }
            }
        }
    }
}