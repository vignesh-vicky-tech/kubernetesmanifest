node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'git-hub', passwordVariable: 'vicky@1234567890', usernameVariable: 'vignesh-vicky-tech')]) {
                        sh "git config user.email vigneshs1711@gmail.com"
                        sh "git config user.name vignesh-vicky-tech"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+vigneshvicky12345/test.*+vigneshvicky12345/test:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
      }
    }
  }
}
}
