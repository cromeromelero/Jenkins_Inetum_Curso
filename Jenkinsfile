pipeline {
    agent any
	environment{
		def CLIMA_ACTUAL="SOLEADO"
		def POBLACION_ACTUAL=5500
	}

    stages {
        stage('InformarClima') {
            steps {
                echo 'Inicio de la stage InformarClima'
                script{
                    num1 = 2
                    num2 = 4
                    total = num1 + num2
					SALIDA = total
                    bat """
					echo El clima actual es: ${CLIMA_ACTUAL}
					"""
                }
            }
        }
        stage('InformarPoblacion') {
            steps {
                echo 'Inicio de la stage InformarPoblacion'
                script{
					bat """
                    echo La poblacion actual es:  ${POBLACION_ACTUAL}
					"""
                }
            }
        }
        
    }
}
