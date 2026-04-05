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
}
