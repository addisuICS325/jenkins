node('jenkins-slave') {
    
     stage('Test Pipeline') {
        sh(script: """
            echo "Testing dotnet build image example"
           git clone https://github.com/addisuICS325/dotnet-example.git
           cd ./dotnet-example
           
           docker build -t test/myappt:1.0 .
           #docker run --tty --rm -p 8000:80 myappt:1.0
        """)
    }
}
