podTemplate(label: 'mypod', cloud: 'kubernetes',
  containers: [
    containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true, privileged: true),
    containerTemplate(name: 'kubectlhelm', image: 'dtzar/helm-kubectl:latest', command: 'cat', ttyEnabled: true, privileged: true),
  ],
  volumes: [hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')]) {
  node('mypod') {
      checkout scm

      def NAMESPACE = "espace"
      def RELEASE_NAME = "espace"
      def BRANCH_NAME = "espacecd"
      
      container("kubectlhelm"){

              stage("Ensure clean K8s cluster"){  
                  try {
                      sh "kubectl delete ns ${NAMESPACE}"
                  }   
                  catch(e){
                      echo "NS does not exist"
                  }                                  
                echo "Cleanup done"
              }
              
              if( BRANCH_NAME == "espacecd") {
              stage("Deploy helm chart"){            
                    sh "kubectl create ns ${NAMESPACE}"
                    sh "helm install ${RELEASE_NAME} ${RELEASE_NAME} -n ${NAMESPACE}"
                    echo "App Deployed"                  
              }
              }

      }

    }
  }