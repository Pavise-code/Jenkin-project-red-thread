pipeline {
    agent any

    environment {
        // On définit le nom du projet pour Docker Compose
        COMPOSE_PROJECT_NAME = "cotisations-uai"
    }

    stages {
        stage('Nettoyage Initial') {
            steps {
                echo 'Nettoyage des anciens conteneurs pour repartir sur une base propre...'
                // On s'assure que rien ne tourne déjà sur le port 8081
                sh 'docker-compose down --remove-orphans'
            }
        }

        stage('Construction (Build)') {
            steps {
                echo 'Construction des images (PHP Custom)...'
                // Construit l'image définie dans ton dossier ./php/Dockerfile
                sh 'docker-compose build'
            }
        }

        stage('Déploiement Local') {
            steps {
                echo 'Lancement du site de cotisations...'
                // Lance les services (db, php, nginx) en arrière-plan (-d)
                sh 'docker-compose up -d'
            }
        }

        stage('Vérification') {
            steps {
                echo 'Vérification du statut des services...'
                sh 'docker ps --filter "name=cotisations_"'
                echo "Le site devrait être accessible sur : http://localhost:8081"
            }
        }
    }

    post {
        failure {
            echo "Le déploiement a échoué. Vérification des logs..."
            sh 'docker-compose logs --tail=20'
        }
        success {
            echo "Déploiement terminé avec succès !"
        }
    }
}