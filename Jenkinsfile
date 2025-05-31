pipeline {
    agent any // Utilise n'importe quel agent disponible sur Jenkins (Windows)

    environment {
        // Déclare ici les variables d'environnement spécifiques à Windows
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-17'          // Chemin vers ton JDK 17 local
        PYTHON_HOME = 'C:\\Program Files\\Python312\\python.exe'                // Chemin vers ton Python 3.12 local
        PATH = "${env.PATH};${JAVA_HOME}\\bin;${PYTHON_HOME}"      // Ajoute Java et Python au PATH
    }

    stages {

        // Étape 1 : Récupère le code source depuis ton dépôt GitHub
        stage('Checkout') {
            steps {
                // Cloner la branche main de ton dépôt GitHub
                git branch: 'main', url: 'https://github.com/Hanane-Chaouche/-jenkins-hello-world.git'
            }
        }

        // Étape 2 : Compile et exécute les programmes Java et Python
        stage('Build') {
            steps {
                script {
                    // Affiche que le script s'exécute sur Windows
                    bat 'echo "Running on Windows"'

                    // Compilation du fichier Java
                    bat 'javac --release 8 HelloWorld.java'

                    // Exécution du programme Java
                    bat 'java HelloWorld'

                    // Exécution du script Python
                    bat 'python hello.py'
                }
            }
        }
    }
}

