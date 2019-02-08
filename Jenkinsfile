pipeline {
    agent {
            docker {
                image 'pdmlab/jenkins-node-docker-agent:6.11.1'
                args '-v /paserver/docker/volumes/elk:/paserver/docker/volumes/elk'
            }
        }
    stages {
        stage('Copy ELK stack configs') {
                    steps {
                         sh 'mkdir -p /paserver/docker/volumes/elk/elasticsearch/config'
                         sh 'cp -r ./elasticsearch/config /paserver/docker/volumes/elk/elasticsearch/'
                         sh 'mkdir -p /paserver/docker/volumes/elk/kibana/config'
                         sh 'cp -r ./kibana/config/ /paserver/docker/volumes/elk/kibana/'
                         sh 'mkdir -p /paserver/docker/volumes/elk/logstash/config'
                         sh 'cp -r ./logstash/config/ /paserver/docker/volumes/elk/logstash/'
                         sh 'mkdir -p /paserver/docker/volumes/elk/logstash/pipeline'
                         sh 'cp -r ./logstash/pipeline/ /paserver/docker/volumes/elk/logstash/'
                    }

        }
        stage('Build EKL stack') {
            steps {
                 sh 'docker-compose up -d'
            }
        }
    }
}