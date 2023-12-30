pipeline {
    agent any
    
    environment {
        
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'latest', url: 'https://github.com/rameshkumarvermagithub/10-MicroService-Appliction'
            }
        }
        
        stage('SonarQube') {
            steps {
                
                withSonarQubeEnv('sonar-server') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=10-Tier -Dsonar.projectName=10-Tier -Dsonar.java.binaries=. '''
                }
               
            }
        }
        
        stage('adservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/adservice/') {
                                 sh "docker build -t rameshkumarverma/adservice:latest ."
                                 sh "docker push rameshkumarverma/adservice:latest"
								                 sh "docker rmi rameshkumarverma/adservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('cartservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/cartservice/src/') {
                                 sh "docker build -t rameshkumarverma/cartservice:latest ."
                                 sh "docker push rameshkumarverma/cartservice:latest"
								                 sh "docker rmi rameshkumarverma/cartservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('checkoutservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/checkoutservice/') {
                                 sh "docker build -t rameshkumarverma/checkoutservice:latest ."
                                 sh "docker push rameshkumarverma/checkoutservice:latest"
								                 sh "docker rmi rameshkumarverma/checkoutservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('currencyservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/currencyservice/') {
                                 sh "docker build -t rameshkumarverma/currencyservice:latest ."
                                 sh "docker push rameshkumarverma/currencyservice:latest"
								                 sh "docker rmi rameshkumarverma/currencyservice:latest"
                        }
                    }
                }
            }
        }
        
		stage('emailservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/emailservice/') {
                                 sh "docker build -t rameshkumarverma/emailservice:latest ."
                                 sh "docker push rameshkumarverma/emailservice:latest"
								                 sh "docker rmi rameshkumarverma/emailservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('frontend') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/frontend/') {
                                 sh "docker build -t rameshkumarverma/frontend:latest ."
                                 sh "docker push rameshkumarverma/frontend:latest"
								                 sh "docker rmi rameshkumarverma/frontend:latest"
                        }
                    }
                }
            }
        }
		
		stage('loadgenerator') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/loadgenerator/') {
                                 sh "docker build -t rameshkumarverma/loadgenerator:latest ."
                                 sh "docker push rameshkumarverma/loadgenerator:latest"
								                 sh "docker rmi rameshkumarverma/loadgenerator:latest"
                        }
                    }
                }
            }
        }
		
		stage('paymentservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/paymentservice/') {
                                 sh "docker build -t rameshkumarverma/paymentservice:latest ."
                                 sh "docker push rameshkumarverma/paymentservice:latest"
								                  sh "docker rmi rameshkumarverma/paymentservice:latest"
                        }
                    }
                }
            }
        }
        
		stage('productcatalogservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/productcatalogservice/') {
                                 sh "docker build -t rameshkumarverma/productcatalogservice:latest ."
                                 sh "docker push rameshkumarverma/productcatalogservice:latest"
								                 sh "docker rmi rameshkumarverma/productcatalogservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('recommendationservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/recommendationservice/') {
                                 sh "docker build -t rameshkumarverma/recommendationservice:latest ."
                                 sh "docker push rameshkumarverma/recommendationservice:latest"
								                 sh "docker rmi rameshkumarverma/recommendationservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('shippingservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier/src/shippingservice/') {
                                 sh "docker build -t rameshkumarverma/shippingservice:latest ."
                                 sh "docker push rameshkumarverma/shippingservice:latest"
								                 sh "docker rmi rameshkumarverma/shippingservice:latest"
                        }
                    }
                }
            }
        }
        
        
        	stage('K8-Deploy') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8s', namespace: '', restrictKubeConfigAccess: false, serverUrl: '') {
                         sh 'kubectl apply -f deployment-service.yml'
                         sh 'kubectl get pods'
                         sh 'kubectl get svc'
                }
            }
        }
        
    }
}
