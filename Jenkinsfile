pipeline {
    agent any
    environment {
        REMOTE_USER = 'jenkins'     // e.g., ubuntu, ec2-user
        REMOTE_HOST = 'https://env-1477092.ktm.yetiappcloud.com'       // IP or domain
        SSH_KEY_ID = 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDqMYH6rnte/ygvPeKS7r84OSk81EMCsx9eQoQehr97/Vn4MIa6g0WyZ68WDcTBwMYcD7ccMO1LusooyRmWM69P1cnefzPw4Ssm6Tbn6RGl4OOlJWyU6vZQgJ9MOmXMy58
0Jv7dlY8qfzoKzkc8oKK5YLaia0eDI8k2gkuhM82J9G2oNMWsXF881jWHed9mdOwBy5Jlmg1Bpj6gk6HnP9Pk4STUObdAsynaW9XLWeYjOKMSZX8TOD84hhx0P4i/skEoseacOvKBqJSX/Yg8RdR0kHdhZt/DGkVRvlXZYC
acFtBV/rSA1gxzsD/6VwNHEtPVSXZyajK8ssboR3BK1PYSOC/953mDgwhURy3jAMRnMM8fuyVxOW8CTdhwoglEvCVBgXRT7uxYfI+obtYssC8KsnUv23roPptVqo8GXI/FqpJLiBC9QT5wnrrjkRY47ZLBOt/mkw8Lkxb1k
AS/fnGy+ma0tEnFtydA+x0Z8P/D74J9dsXp3lQyJcA9pACAwnM= jenkins@node21981-env-1477092.ktm.yetiappcloud.com'             // Jenkins credential ID
        FOLDER_NAME = 'milans'                // Folder to create
    }
    stages {
        stage('Create Folder on Remote Server') {
            steps {
                sshagent(credentials: ["${env.SSH_KEY_ID}"]) {
                    sh """
                    echo "Creating folder on remote server..."
                    ssh -o StrictHostKeyChecking=no ${REMOTE_USER}@${REMOTE_HOST} \\
                        "mkdir -p ~/${FOLDER_NAME} && echo 'Folder created at ~/${FOLDER_NAME}'"
                    """
                }
            }
        }
    }
}
