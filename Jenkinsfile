properties([parameters([[$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', description: 'taking branch from git repo', filterLength: 1, filterable: false, name: 'branch', randomName: 'choice-parameter-102185544867300', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: ''], script: [classpath: [], sandbox: false, script: '''
def gettags = ("git ls-remote -t -h https://github.com/aravindhsz/NodeApp.git").execute()
return gettags.text.readLines().collect { 
  it.split()[1].replaceAll(\'refs/heads/\', \'\').replaceAll(\'refs/tags/\', \'\').replaceAll("\\\\^\\\\{\\\\}", \'\')
}''']]]])])
pipeline
{
    environment
    {
        imagename="aravindhsz/image-4"
        registryCredential='dockerhub'
        dockerImage=''
    }
    agent any
    stages{

    stage('Cloning Git') {
	
        /* Cloning the Repository to our Workspace */
        steps{

        git 'https://github.com/aravindhsz/Hello-world.git'
               }
         }
    stage('Build image') {
        /* This builds the actual image */
        steps{

        script {
dockerImage = docker.build imagename
                }
            }
        }
	    /*
    stage('Push image') {
        steps
        {
        script
        {
        docker.withRegistry( '', registryCredential){
        dockerImage.push()
        
        }
        }
       }
       
    }*/
  }
}
