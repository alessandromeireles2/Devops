node {
stage('Build') {
echo 'Building..'
deleteDir()
checkout scm
sh 'cat README.md'
}
stage('Setup'){
mvn install
}  
stage('Test') {
echo 'Testing..'
mvn test
}
stage('Deploy') {
echo 'Deploying....'
}
}
