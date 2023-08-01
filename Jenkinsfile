node {
    def app
    
    env.IMAGE = 'tundeficky/amazon-clone'

    stage('Clone repository') {
             git branch: 'main', url: 'https://github.com/OlatundeTai-Lawal/Amazon-argocd-manifest.git'  
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'Ola-github-token', passwordVariable: 'SECRET TEXT', usernameVariable: 'GIT_USERNAME')]) {
                        //script {def encodedPassword = URLEncoder.encode("$SECRET TEXT",'UTF-8')}
                        //script  {def IMAGE='tundeficky/amazon-clone'}
                        sh "git config user.email tundeficky@gmail.com"
                        sh "git config user.name Olatunde Tai-Lawal"
                        //sh "git switch master"
                        sh "cat deployment.yml"
                        sh "sed -i 's+${IMAGE}.*+${IMAGE}:${DOCKERTAG}+g' deployment.yml"
                        sh "cat deployment.yml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${SECRET TEXT}@github.com/${GIT_USERNAME}/argocd-amazon-manifest.git HEAD:main"
             }
         }
     }
  }
}
