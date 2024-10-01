pipeline {
    agent any
	environment{
		def POBLACION_ACTUAL=5500
	}

    stages {
        stage('GeneraFicheroEstadisticoPoblacion') {
            steps {
                echo 'Inicio de la stage GeneraFicheroEstadisticoPoblacion'
                script{
                    def currentDate = new Date().format('yyyy_MM_dd') 
                    def outFile = "poblacion_neta_${currentDate}.txt" 
					def poblacionNeta = POBLACION_ACTUAL.toInteger() * 0.8

					bat """
                    echo La poblacion neta es:  ${poblacionNeta} > C:\\${outFile}
					"""
                }
            }
        }
        
    }
}
