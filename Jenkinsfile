pipeline {
    agent any
    stages {
        stage('Build with different options') {
            steps {
                sh '''
                    echo 'build.sh (default options)'
                    rm conf.sh 2> /dev/null || true
                    ln -sf conf.sh.default conf.sh
                    ./dscripts/build.sh  -p
                '''
                sh '''
                    echo 'build.sh -b # include label BUILDINFO'
                    ./dscripts/build.sh  -pr
                '''
                sh '''
                    echo 'build.sh -r # remove existing image (default tag)'
                    ./dscripts/build.sh  -pr
                '''
                sh '''
                    echo 'build.sh -c # --no-cache'
                    ./dscripts/build.sh  -pc
                '''
                sh '''
                    echo 'build.sh -M # no manifest'
                    ./dscripts/build.sh  -pM
                '''
                sh '''
                    echo 'build.sh -P # push after build'
                    ./dscripts/build.sh  -pP
                '''
                sh '''
                    echo 'build.sh -t mytag # tag, no manifest'
                    ./dscripts/build.sh  -pt mytag
                '''
                sh '''
                    echo 'build.sh -rt mytag # remove existing image (custom tag)'
                    ./dscripts/build.sh  -pr
                '''
            }
        }
    }
}