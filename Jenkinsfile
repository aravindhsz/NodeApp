properties([parameters([[$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', description: 'taking branch from git repo', filterLength: 1, filterable: false, name: 'branch', randomName: 'choice-parameter-102185544867300', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: ''], script: [classpath: [], sandbox: false, script: '''
def gettags = ("git ls-remote -t -h https://USER:PASS@bitbucket.org/project_name.git").execute()
return gettags.text.readLines().collect { 
  it.split()[1].replaceAll(\'refs/heads/\', \'\').replaceAll(\'refs/tags/\', \'\').replaceAll("\\\\^\\\\{\\\\}", \'\')
}''']]]])])
node {
    def app
	
	

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("aravindhsz/new_pro")
    }

   /*
    stage('Push image') {
        
			You would need to first register with DockerHub before you can push images to your account
		
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }
*/
}
