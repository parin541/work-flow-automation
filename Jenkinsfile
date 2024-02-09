pipeline {
    agent any
    parameters {
      string(name: 'PLANET', defaultValue: 'Earth', description: 'Which planet are we on?')
      string(name: 'GREETING', defaultValue: 'Hello', description: 'How shall we greet?')
    }
    triggers {
        parameterizedCron('''
           # Everyday at 5 AM
           0 5 * * * %GREETING=Hola;PLANET=Pluto
           # Every other day at 5:05 AM
           5 5 */2 * * %GREETING=Namaste;PLANET=GURU
        ''')
    }
    stages {
        stage('Example') {
            steps {
                echo "${params.GREETING} ${params.PLANET}"
                script { currentBuild.description = "${params.GREETING} ${params.PLANET}" }
            }
        }
    }
}
