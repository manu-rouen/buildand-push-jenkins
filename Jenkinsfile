node {

   def registryProjet='buildjenkins/'
   def IMAGE="${registryProjet}app:4.2"

    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
          }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID") { c ->
       
          }
    }

    stage('Push') {
       docker.withRegistry('https://registry.ludovic.io/' , 'b6092eb6-13eb-457b-b5ef-d28012bb7e9c') {
              img.push 'latest'
              img.push()
          }
    }
   stage('compuse_up') {
       sh 'docker compose up --detach'
    }

}

