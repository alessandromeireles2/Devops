def username = 'Jenkins'
env.CC = 'clang'
node {
stage('Build') {
env.DEBUG_FLAGS = '-g'
echo 'Building..'
echo "Hello Mr. ${username}"
echo "Running ${env.JOB_NAME} (${env.BUILD_ID}) at ${env.JENKINS_URL}"  
deleteDir()
checkout scm
sh 'cat README.md'
sh 'printenv'
}
stage('Test') {
echo 'Testing..'
}
stage('Deploy') {
echo 'Deploying....'
}
}
