pipeline
agent any
parameters{
choice (name: 'NUMBER',
        choices: [10, 20, 30, 40, 50, 60, 70, 80, 90, 100],
         descriptions: 'Select the value for F(n) for the Fibonacci sequence.')
         }
         options {
         buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
         timeout(time: 12, unit: 'HOURS')
         timeStamps()
         }
         triggers {
         cron: 'MIDNIGHT'
         }
         stages{
          stage('Make executable'){
            steps{
              sh('chmod +x ./scripts/fibonacci.sh')
              }
             }
           stage('Relative path'){
              steps{
                sh("./scripts/fibonacci.sh', ${env.NUMBER})
                }
              }
           stage('Full path'){
              steps{
                 sh("${env.WORKSPACE}/scripts/fibonacci.sh ${env.NUMBER}")
                 }
              }
           stage('Change Directory'){
               steps{
                  dir("${env.WORKSPACE}/scripts){
                      sh("./fibonacci.sh ${env.NUMBER}")
                   }
               }
           }
       }
  }
       
