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
                        """
                    }
            }
        }
 
    }
}
