def createNamespace (name) {
    echo "Creating namespace ${name} if needed"
    sh "kubectl create namespace ${name} --dry-run -o yaml | kubectl apply -f -"
}


node {



    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */
        checkout scm
        
         sh "kubectl get nodes"
        // sh "export aws_profile=${env.aws_profile}"
        // sh "export aws_region=${env.aws_region}"
        // sh "export KOPS_STATE_STORE=${env.S3BucketName}"
        // sh "AWS_PROFILE=${env.aws_profile} AWS_ACCESS_KEY_ID=${env.awsKey} AWS_SECRET_ACCESS_KEY=${env.awsSecret} kops export kubecfg ${env.YOUR_CLUSTER_NAME} --state=${env.S3BucketName}"
        
    }

    try {
        stage ('helm test') {
                createNamespace (monitoring)
            }

   
        }
        catch (Exception err){
            err_msg = "Test had Exception(${err})"
            currentBuild.result = 'FAILURE'
            error "FAILED - Stopping build for Error(${err_msg})"
    }
}