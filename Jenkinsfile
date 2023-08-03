node {
    def app

    stage('Clone repository') {
     checkout scm 
     //git branch: 'main', url: 'https://github.com/Mikey-06/coffee-app-kubernetesmanifest.git'
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email manyanwu06@gmail.com"
                        sh "git config user.name Mikey-06"
                        //sh "git switch master"
                        sh "cat deployment.yml"
                      //sh "sed -i 's+raj80dockerid/test.*+raj80dockerid/test:${DOCKERTAG}+g' deployment.yaml"
                        sh "sed -i 's+mikey6/coffee-club-reg-app.*+mikey6/coffee-club-reg-app:${DOCKERTAG}+g' deployment.yml"
                        sh "cat deployment.yml"
                        sh "git add ."
                        sh "git diff --cached"
                        sh "git commit -m 'Done by Jenkins Job Coffee_Club_Reg_App(Update-Manifest): ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/coffee-app-kubernetesmanifest.git HEAD:main"
      }
    }
  }
}
}
