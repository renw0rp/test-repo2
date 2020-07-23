properties([pipelineTriggers([githubPush()])])

pipeline {

    agent any


    stages {
        stage('Init') {

            steps {
               
                    sh """
                        echo "BRANCH NAME: ${env.BRANCH_NAME}"
                        echo "CHANGE_ID: ${env.CHANGE_ID}"
                        echo "CHANGE_URL: ${env.CHANGE_URL}"
                        echo "CHANGE_TITLE: ${env.CHANGE_TITLE}"
                        echo "CHANGE_AUTHOR: ${env.CHANGE_AUTHOR}"
                        echo "CHANGE_AUTHOR_DISPLAY_NAME: ${env.CHANGE_AUTHOR_DISPLAY_NAME}"
                        echo "CHANGE_AUTHOR_EMAIL: ${env.CHANGE_AUTHOR_EMAIL}"
                        echo "CHANGE_TARGET: ${env.CHANGE_TARGET}"
                        
                        echo "BUILD_NUMBER: ${env.BUILD_NUMBER}"
                        echo "BUILD_ID: ${env.BUILD_ID}"
                        echo "BUILD_DISPLAY_NAME: ${env.BUILD_DISPLAY_NAME}"
                        echo "JOB_NAME: ${env.JOB_NAME}"
                        echo "JOB_BASE_NAME: ${env.JOB_BASE_NAME}"
                        echo "BUILD_TAG: ${env.BUILD_TAG}"

                        echo "currentBuild.number: ${currentBuild.number}"
                        echo "currentBuild.displayName: ${currentBuild.displayName}"
                        echo "currentBuild.fullDisplayName: ${currentBuild.fullDisplayName}"v
                        echo "currentBuild.projectName: ${currentBuild.projectName}"
                        echo "currentBuild.fullProjectName: ${currentBuild.fullProjectName}"
                        echo "currentBuild.id: ${currentBuild.id}"

                        echo "currentBuild.buildCauses: ${currentBuild.buildCauses}"
                        echo "currentBuild.getBuildCauses: ${currentBuild.getBuildCauses('hudson.model.Cause$UserCause')}"
                        echo "currentBuild.changeSets: ${currentBuild.changeSets}"
                    """
                }
            
        }

        stage('Build') {


            environment {
                gitCreds = 'renw0rp-github-credentials'
            }

            steps {
              

                withSonarQubeEnv(credentialsId: 'sonarqube-token', installationName: 'SonarQube') {
                    sshagent(credentials: [gitCreds]) {

                        sh """
                        echo "DISPLAYING FROM JENKINSFILE"
                        echo "running ls"
                        ls

                        echo "running pwd"
                        pwd

                        echo "running git branch"
                        git branch

                        echo "running git remote -v"
                        git remote -v


            
                        echo "running git remote -v"
git remote -v

echo "running git status"
git status

#sbt clean compile assembly sonarScan -Dsonar.branch.name="$BRANCH_NAME"

echo 'Set up upstream branch for local testxxx9 branch and check status'
git checkout testxxx9 # a bit hacky; Jenkins seems to checkout branch with detached HEAD
git branch --set-upstream-to=origin/testxxx9 testxxx9
git config branch.testxxx9.remote origin
git config branch.testxxx9.merge refs/heads/testxxx9

git branch && git status && git remote -v

echo "$BUILD_DISPLAY_NAME" > build.txt

echo "running ls -Altr"
ls -Altr

git add build.txt

echo "running git status"
git status

echo "running git commit"
git commit -m "Build: ${BUILD_DISPLAY_NAME}"

echo "running git push"
git push origin testxxx9
                    """
                    }
                }
            }
        }
 
    }
}




