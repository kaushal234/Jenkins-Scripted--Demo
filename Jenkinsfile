node {
    try {
        stage('Checkout') {
            checkout scm
        }

        stage('Show Files') {
            echo "Displaying the files in the workspace"

            if (isUnix()) {
                sh 'ls -ltr'
            } else {
                bat 'dir'
            }
        }

        stage('Install Dependencies') {
            echo "Installing dependencies"

            if (isUnix()) {
                sh 'python3 -m pip install -r requirements.txt'
            } else {
                bat 'python3 -m pip install -r requirements.txt'
            }
        }
        stage('Run Application') {
            echo "Running the application"

            if (isUnix()) {
                sh 'python3 app.py'
            } else {
                bat 'python3 app.py'
            }
        }
        stage('Run Tests') {
            echo "Running tests"

            if (isUnix()) {
                sh 'python3 pytest test_app.py'
            } else {
                bat 'python3 pytest test_app.py'
            }
        }
        stage('build result'){
            echo "Build result: SUCCESS"
        }

    } catch (Exception e) {
        echo "Build failed: ${e.getMessage()}"
        throw e
    } finally {
        echo "Pipeline execution completed."
    }
    
}
