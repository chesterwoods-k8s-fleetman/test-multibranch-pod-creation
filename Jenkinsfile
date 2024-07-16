pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: maven
            image: maven:alpine
            command:
            - cat
            tty: true
		---	
		apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: nginx
            image: nginx:1.14.2
            ports:
			- containerPort: 80
        '''
    }
  }
  stages {
    stage('Run maven') {
      steps {
        container('maven') {
          sh 'mvn -version'
        }
      }
    }
  }
}