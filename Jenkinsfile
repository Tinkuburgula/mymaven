node('built-in')
{
 stage('ContinuousDownload') 
 {
  git 'https://github.com/intelliqittrainings/maven.git'
  }
 stage('ContinuousBuild') 
 {
  sh 'mvn package'
  }
stage('ContinuousDeployment') 
 {
  deploy adapters: [tomcat9(credentialsId: '8d567cad-77ee-4f59-9397-f7c150601a4e', path: '', url: 'http://172.31.93.207:8080')], contextPath: 'testapp', war: '**/*.war'
  }
stage('ContinuousTesting') 
 {
  git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
  sh 'java -jar /var/lib/jenkins/workspace/Scripted1/testing.jar'
  }
  stage('ContinuousDelivery') 
 {
  deploy adapters: [tomcat9(credentialsId: '8d567cad-77ee-4f59-9397-f7c150601a4e', path: '', url: 'http://172.31.82.162:8080')], contextPath: 'prodapp', war: '**/*.war'
  }
}
