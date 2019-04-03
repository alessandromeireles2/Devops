node {
stage('Build') {
echo 'Building..'
deleteDir()
checkout scm
sh 'cat README.md'
}
stage('Test') {
echo 'Testing..'
mvn install
mvn test
}
stage('Deploy') {
echo 'Deploying....'
}
}
