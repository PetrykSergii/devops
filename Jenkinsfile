pipeline {
    agent any
    options {
        // Timeout counter starts AFTER agent is allocated
        skipDefaultCheckout(true)
    }
    stages {
        
        stage('Cleaning workspace') {
            steps {
               echo "**************** Start cleaning ***************************"
               sh "rm -Rf /Jenkins/*"
               sh "rm -Rf /Jenkins/.git"
               echo "**************** cleaning is completed ***************************"
                    }
        }
        
        stage('Cloning from Hithub') {
            steps {
               echo "**************** Start cloning from Hithub ***************************"
               sh "git clone https://github.com/PetrykSergii/test.git /Jenkins"
               echo "**************** Clonin from Hithub is completed ***************************"
                    }
                                            }
                    
        stage('Deploying web site') {
            steps {
                echo "**************** Start deploying web site ***************************"
                sh "ansible-playbook /Jenkins/web.yml -u sergii --private-key /var/lib/jenkins/key/id_rsa"
                echo "**************** Deploying web site is completed ***************************"
                    }  

                                            }
    }
}
