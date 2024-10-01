pipeline {
    agent any

	environment{
		def SALIDA=""
	}

    stages {
        stage('Suma') {
            steps {
                echo 'Inicio de la stage Suma'
                script{
                    num1 = 2
                    num2 = 4
                    total = num1 + num2
					SALIDA = total
                    println('La suma de ' + num1 + ' y ' + num2 +' es: ' + total)
					bat """
							echo La suma del num1 y  num2  es:  ${SALIDA} >> C:\\resultados_FechaDeHoy.txt
						"""
                }
            }
        }
        stage('Resta') {
            steps {
                echo 'Inicio de la stage Resta'
                script{
                    num1 = 12
                    num2 = 8
                    total = num1 - num2
					SALIDA = total

                    println('La resta de ' + num1 + ' y ' + num2 +' es: ' + total)
					bat """
							echo La resta del num1 y  num2  es:  ${SALIDA} >> C:\\resultados_FechaDeHoy.txt
						"""
                }
            }
        }
        stage('Multiplicacion') {
            steps {
                echo 'Inicio de la stage Multiplicacion'
                script{
                    num1 = 2
                    num2 = 4
                    total = num1 * num2
					SALIDA = total

                    println('La multiplicacion de ' + num1 + ' y ' + num2 +' es: ' + total)
					bat """
							echo La multiplicacion del num1 y  num2  es:  ${SALIDA} >> C:\\resultados_FechaDeHoy.txt
						"""
                }
            }
        }
        stage('Division') {
            steps {
                echo 'Inicio de la stage Division'
                script{
                    num1 = 9
                    num2 = 3
                    boolFlag = false
                    if(num1 == 0 || num2 == 0){
                        boolFlag = true
                    }
                    if(boolFlag){
                        println('La division no es posible cuando uno de los operandos sea 0')
                    }else {
                        total = num1 / num2
						SALIDA = total

                        println('La divion de ' + num1 + ' y ' + num2 +' es: ' + total)
						bat """
							echo La division del num1 y  num2  es:  ${SALIDA} >> C:\\resultados_FechaDeHoy.txt
						"""
                    }
                    
                }
            }
        }
        stage('generacionFicheroSalida') {
			steps{
				script {
                    bat """
                        
                    """

                    def fileContent = readFile('C:\\resultados_FechaDeHoy.txt')
                    
                    echo "File content is: ${fileContent}"
                }
			
			}
		}
    }
}
