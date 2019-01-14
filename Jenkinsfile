pipeline {
    agent {
        docker {
            image "ruby"
            args "--link selenium"
        }
    }
    stages {
        stage("Build") {
            steps {
                sh "bundle install"
            }
        }
        stage("Run Tests") {
            steps {
                sh "bundle exec cucumber -p ci"
                cucumber fileIncludePattern: '**/*.json', jsonReportDirectory: 'log', sortingMethod: 'ALPHABETICAL'
            }
        }
    }
}
