node{
   
   stage('Clone') {
       
     git branch: 'feature/2025.10.20', url: 'https://github.com/srinfotechbatch4/onlinebookstore.git'
   }
   stage('Build') {
       
    bat 'mvn clean install'
   }
    stage('Test') {
       
    bat 'mvn test'
   }
   
    stage('Artifacts') {
       
     archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
   }
    
}