pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/RAMESHKUMARVERMAGITHUB/three-tier-architecture-demo.git'
            }
        }   
        stage('SonarQube') {
            steps {     
                withSonarQubeEnv('sonar-server') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=three-tier-architecture-demo -Dsonar.projectName=three-tier-architecture-demo -Dsonar.java.binaries=. '''
                }
            }
        }
        stage('cart') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/cart/') {
                                 sh "docker build -t rameshkumarverma/cart:latest ."
                                 sh "docker push rameshkumarverma/cart:latest"
				 sh "docker rmi rameshkumarverma/cart:latest"
                        }
                    }
                }
            }
        }
	stage('catalogue') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/catalogue/') {
                                 sh "docker build -t rameshkumarverma/catalogue:latest ."
                                 sh "docker push rameshkumarverma/catalogue:latest"
				 sh "docker rmi rameshkumarverma/catalogue:latest"
                        }
                    }
                }
            }
        }	
	stage('dispatch') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/dispatch/') {
                                 sh "docker build -t rameshkumarverma/dispatch:latest ."
                                 sh "docker push rameshkumarverma/dispatch:latest"
				 sh "docker rmi rameshkumarverma/dispatch:latest"
                        }
                    }
                }
            }
        }
	    stage('fluentd') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/fluentd/') {
                                 sh "docker build -t rameshkumarverma/fluentd:latest ."
                                 sh "docker push rameshkumarverma/fluentd:latest"
				 sh "docker rmi rameshkumarverma/fluentd:latest"
                        }
                    }
                }
            }
        }
	    stage('load-gen') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/load-gen/') {
                                 sh "docker build -t rameshkumarverma/load-gen:latest ."
                                 sh "docker push rameshkumarverma/load-gen:latest"
				 sh "docker rmi rameshkumarverma/load-gen:latest"
                        }
                    }
                }
            }
        }
	    stage('mongo') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/mongo/') {
                                 sh "docker build -t rameshkumarverma/mongo:latest ."
                                 sh "docker push rameshkumarverma/mongo:latest"
				 sh "docker rmi rameshkumarverma/mongo:latest"
                        }
                    }
                }
            }
        }
	    stage('mysql') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/mysql/') {
                                 sh "docker build -t rameshkumarverma/mysql:latest ."
                                 sh "docker push rameshkumarverma/mysql:latest"
				 sh "docker rmi rameshkumarverma/mysql:latest"
                        }
                    }
                }
            }
        }
	    stage('payment') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/payment/') {
                                 sh "docker build -t rameshkumarverma/payment:latest ."
                                 sh "docker push rameshkumarverma/payment:latest"
				 sh "docker rmi rameshkumarverma/payment:latest"
                        }
                    }
                }
            }
        }
	    stage('ratings') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/ratings/') {
                                 sh "docker build -t rameshkumarverma/ratings:latest ."
                                 sh "docker push rameshkumarverma/ratings:latest"
				 sh "docker rmi rameshkumarverma/ratings:latest"
                        }
                    }
                }
            }
        }
	    stage('shipping') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/shipping/') {
                                 sh "docker build -t rameshkumarverma/shipping:latest ."
                                 sh "docker push rameshkumarverma/shipping:latest"
				 sh "docker rmi rameshkumarverma/shipping:latest"
                        }
                    }
                }
            }
        }
	    stage('user') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/user/') {
                                 sh "docker build -t rameshkumarverma/user:latest ."
                                 sh "docker push rameshkumarverma/user:latest"
				 sh "docker rmi rameshkumarverma/user:latest"
                        }
                    }
                }
            }
        }
	    stage('web') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('three-tier-architecture-demo/web/') {
                                 sh "docker build -t rameshkumarverma/web:latest ."
                                 sh "docker push rameshkumarverma/web:latest"
				 sh "docker rmi rameshkumarverma/web:latest"
                        }
                    }
                }
            }
        }
	    stage('deploy to container'){
		    steps{
			    sh "docker-compose pull && docker-compose up -d"
		    }
	    }    
        // stage('K8-Deploy') {
        //     steps {
        //         withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8s', namespace: '', restrictKubeConfigAccess: false, serverUrl: '') {
        //                  sh 'kubectl apply -f deployment-service.yml'
        //                  sh 'kubectl get pods'
        //                  sh 'kubectl get svc'
        //         }
        //     }
        // }
        
    }
}
