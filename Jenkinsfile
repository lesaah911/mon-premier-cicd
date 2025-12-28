pipeline {
    agent any
    
    stages {
        stage('Préparation') {
            steps {
                echo '🚀 Début du déploiement...'
                echo "Déploiement du build numéro ${env.BUILD_NUMBER}"
            }
        }
        
        stage('Vérification des fichiers') {
            steps {
                echo '📁 Vérification des fichiers...'
                sh '''
                    ls -la
                    cat website/index.html
                '''
            }
        }
        
        stage('Déploiement avec Ansible') {
            steps {
                echo '⚙️ Exécution du playbook Ansible...'
                sh '''
                    ansible-playbook -i inventory.ini deploy.yml
                '''
            }
        }
        
        stage('Test du déploiement') {
            steps {
                echo '✅ Vérification que le site est accessible...'
                sh '''
                    sleep 5
                    curl -f http://204.236.214.199 || exit 1
                '''
            }
        }
    }
    
    post {
        success {
            echo '✅ Déploiement réussi ! 🎉'
            echo 'Votre site est accessible sur http://<IP-APP-SERVER>'
        }
        failure {
            echo '❌ Le déploiement a échoué'
        }
    }
}