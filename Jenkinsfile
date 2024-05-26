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
               sh "rm -Rf /Jenkins2/*"
               sh "rm -Rf /Jenkins2/.git"
               echo "**************** cleaning is completed ***************************"
                    }
        }
        
        stage('Cloning from Hithub') {
            steps {
               echo "**************** Start cloning from Hithub ***************************"
               sh "git clone -b main https://github.com/PetrykSergii/site.git /Jenkins"
               sh "git clone -b dev https://github.com/PetrykSergii/site.git /Jenkins2"
               echo "**************** Clonin from Hithub is completed ***************************"
                    }
                                            }
                    
        stage('Deploying web site') {
            steps {
                echo "**************** Start deploying web site ***************************"
                sh "ansible-playbook /Jenkins/web.yml -u sergii --private-key /var/lib/jenkins/key/id_rsa"
                sh "ansible-playbook /Jenkins2/web.yml -u sergii --private-key /var/lib/jenkins/key/id_rsa"
                echo "**************** Deploying web site is completed ***************************"
                    }  

                                            }
    }
}
