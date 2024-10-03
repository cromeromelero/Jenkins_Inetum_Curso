pipeline {
    agent any

    environment {
        DIA_ACTUAL = new Date().format('EEEE')
        OUTPUT_FILE = "C:\\out.txt"
        valorLinea0 = ''
        valorLinea1 = ''
        valorLinea2 = ''
        valorLinea3 = ''
    }

    stages {
        stage('Leer Fichero') {
            steps {
                script {
                    def filePath = 'C:\\valores.txt'
                    def fileContent = readFile(filePath)
                    def lines = fileContent.split('\n')
                        valorLinea0 = lines[0].trim() as Integer
                        valorLinea1 = lines[1].trim() as Integer
                        valorLinea2 = lines[2].trim() as Integer
                        valorLinea3 = lines[3].trim() as Integer
                }
            }
        }
        stage('Lunes - Poblacion') {
            when {
                expression { return env.DIA_ACTUAL == "lunes" }
            }
            steps {
                script {
                    def calcularPoblacionFinal = valorLinea0 * 0.80
                    bat """
                        echo Lunes: La población final es: ${calcularPoblacionFinal} >> ${OUTPUT_FILE}
                    """
                }
            }
        }
        stage('Martes - Operaciones') {
            when {
                expression { return env.DIA_ACTUAL == "martes" }
            }
            steps {
                script {
                    def suma = valorLinea1 + valorLinea2
                    def resta = valorLinea1 - valorLinea2
                    def multiplicacion = valorLinea1 * valorLinea2
                    def division = valorLinea1 / valorLinea2
                    bat """
                        echo Martes: Suma de ${valorLinea1} y ${valorLinea2} es: ${suma} >> ${OUTPUT_FILE}
                        echo Martes: Resta de ${valorLinea1} y ${valorLinea2} es: ${resta} >> ${OUTPUT_FILE}
                        echo Martes: Multiplicacion de ${valorLinea1} y ${valorLinea2} es: ${multiplicacion} >> ${OUTPUT_FILE}
                        echo Martes: Division de ${valorLinea1} y ${valorLinea2} es: ${division} >> ${OUTPUT_FILE}
                    """
                }
            }
        }
        stage('Miercoles - Temperatura') {
            when {
                expression { return env.DIA_ACTUAL == "miércoles" }
            }
            steps {
                script {
                    def celsius = (valorLinea3 - 32) * (5 / 9)
                    bat """
                        echo Miércoles: La temperatura en Celsius es: ${celsius} >> ${OUTPUT_FILE}
                    """
                }
            }
        }

        // Thursday: Inform the user running the pipeline
        stage('Jueves - Usuario') {
            when {
                expression { return env.DIA_ACTUAL == "juevess" }
            }
            steps {
                script {
                    def currentUser =  currentBuild.rawBuild.getCause(hudson.model.Cause$UserIdCause)
                    echo "Jueves: El usuario que está ejecutando el pipeline es: ${currentUser.getUserId()}"
                    
                }
            }
        }

        // Friday: Generate a basic Maven project from start.spring.io and run clean install
        stage('Viernes - Maven') {
            when {
                expression { return env.DIA_ACTUAL == "jueves" }
            }
            steps {
                script {
                    // Download the Maven project from start.spring.io
                    bat '''
						curl https://start.spring.io/starter.zip -d dependencies=mysql -d type=maven-project -o spring-boot-maven.zip
						powershell -Command "Expand-Archive -Path spring-boot-maven.zip -DestinationPath spring-boot-project"
					'''
					// Navigate to the project folder and run 'mvn clean install'
					dir('spring-boot-project') {
						bat 'mvn clean install'
					}
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline finished"
        }
    }
}
