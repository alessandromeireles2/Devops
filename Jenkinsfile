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
sh "echo 'res' > result"
stash includes: '**/result', name: 'app'
sh 'cat README.md'
sh 'printenv'
          def ambiente = input id: 'test', message: 'Please Provide Parameters', ok: 'Next',
           parameters: [
              choice(name: 'ENVIRONMENT',
                  choices: ['dev','qa'].join('\n'),
                  description: 'Please select the Environment'),
              string(name: 'EXIT',
                  defaultValue: '0',
                  description: 'Please enter the exit code.')
           ]
exitCode = ambiente['EXIT']
echo "${ambiente}"
}
stage('Test') {
node() {
echo 'Testing..'
parallel FrontendTests: { echo 'Testing Frontend..' },
          BackendTests: { echo 'Testing Backend..' }
deleteDir()
unstash 'app'
sh 'cat result'          
}
}
stage('Deploy') {
echo 'Deploying....'
}
}
