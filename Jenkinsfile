node{
    git branch: 'pipeline', url: 'https://github.com/abdoelnezamy07-devOps/simple_Java-app.git'
    stage('build'){
        try{
            sh 'echo "build stage in progress"'
        }
        catch(Exception e){
            sh 'echo "Exception found"'
            throw e
        }
    }
    stage('test'){
        if (env.BRANCH_NAME == feature){
            sh 'echo "test stage"'
        }
        else{
            sh 'echo "skip test stage"'
        }
    }
}

