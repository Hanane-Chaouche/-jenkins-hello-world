pipeline {
    agent any // Utilise n'importe quel agent (Windows ou Linux)

    stages {

        // Étape 1 : Récupération du code depuis GitHub
        stage('Checkout') {
            steps {
                // Clone depuis ton dépôt GitHub sur la branche main
                git branch: 'main', url: 'https://github.com/Hanane-Chaouche/-jenkins-hello-world.git'
            }
        }

        // Étape 2 : Compilation et exécution des programmes
        stage('Build') {
            steps {
                script {
                    // Si le système est Linux
                    if (isUnix()) {
                        withEnv([
                            // Définir JAVA_HOME et PYTHON_HOME pour Linux
                            "JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64",
                            "PYTHON_HOME=/usr/bin",
                            "PATH=${env.PATH}:${JAVA_HOME}/bin:${PYTHON_HOME}"
                        ]) {
                            // Affichage et exécution des commandes Unix
                            sh 'echo "Running on Unix"'
                            sh 'javac HelloWorld.java'        // Compilation Java
                            sh 'java HelloWorld'              // Exécution Java
                            sh 'python3 hello.py'             // Exécution Python
                        }

                    // Sinon, c’est Windows
                    } else {
                        withEnv([
                            // Chemins personnalisés selon ta machine Windows
                            "JAVA_HOME=C:\\Program Files\\Java\\jdk-17",
                            "PYTHON_HOME=C:\\Program Files\\Python312",
                            "PATH=${env.PATH};${JAVA_HOME}\\bin;${PYTHON_HOME}"
                        ]) {
                            // Affichage et exécution des commandes Windows
                            bat 'echo "Running on Windows"'
                            bat 'javac HelloWorld.java'       // Compilation Java
                            bat 'java HelloWorld'             // Exécution Java
                            bat 'python hello.py'             // Exécution Python
                        }
                    }
                }
            }
        }
    }
}
