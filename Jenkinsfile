pipeline {
    agent any

    stages {
        stage('Construir Imagen Docker') {
            steps {
                sh 'docker run --rm -v /var/run/docker.sock:/var/run/docker.sock -v $PWD:/workspace -w /workspace docker:27 docker build -t hola-mundo-node:latest .'
            }
        }

        stage('Ejecutar Contenedor Node.js') {
            steps {
                sh '''
                    # Detener y eliminar cualquier contenedor previo
                    docker run --rm -v /var/run/docker.sock:/var/run/docker.sock docker:27 docker stop hola-mundo-node || true
                    docker run --rm -v /var/run/docker.sock:/var/run/docker.sock docker:27 docker rm hola-mundo-node || true

                    # Ejecutar el contenedor de la aplicación
                    docker run -d --name hola-mundo-node -p 3000:3000 hola-mundo-node:latest
                '''
            }
        }
    }
}