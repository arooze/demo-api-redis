node {
  stage('Checkout') {
    checkout scm
  }

  stage('Build') {
    sh 'docker image build -t arooze/demo-api:latest .'
  }

  stage('Push') {
    withCredentials([usernamePassword(credentialsId: 'd6d1a6fe-16f2-46bc-b199-32edd0603c84', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]) {
//        usernamePassword(credentialsId: 'docker-credentials',
//                         usernameVariable: 'USERNAME',
//                         passwordVariable: 'PASSWORD')]) {
      sh 'docker login -p "${PASSWORD}" -u "${USERNAME}"'
      sh 'docker image push ${USERNAME}/demo-api:latest'
    }
  }

  stage('Deploy') {
    //withCredentials([
    //    file(credentialsId: 'kube-config',
    //         variable: 'KUBECONFIG')]) {
    //  sh 'kubectl apply -f deployment.yaml'
    //}
  }
}
