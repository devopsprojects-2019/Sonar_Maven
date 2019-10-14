node{

	stage('code checkout'){
	
		echo 'checkout the code and clone it inside jenkins'
		git 'https://github.com/devopsprojects-2019/Sonar_Maven.git'
	}

	stage('code build'){
	
		echo 'building and configuring the code'
		withMaven (jdk:'JDK-1.8', maven:'Maven-3.6.1'){
		sh 'mvn clean compile'
		}
	}

	stage('test'){
	
		echo 'test the code'
		withMaven(jdk:'JDK-1.8', maven:'Maven-3.6.1'){
		sh 'mvn test'
		}
	}

	stage('sonar scan'){
		
		echo 'sonar scan for source code quality check'
		withMaven(jdk:'JDK-1.8', maven:'Maven-3.6.1'){
		sh 'mvn verify sonar:sonar -Dsonar.projectKey=devopsprojects-2019_Sonar_Maven -Dsonar.organization=devopsprojects-2019 -Dsonar.host.url=https://sonarcloud.io  -Dsonar.login=043fdf91216f7ea17c29b3431bd925852b813c1f'

			}
	}


	stage('package'){
	
		echo 'package the output'
		withMaven(jdk: 'JDK-1.8', maven:'Maven-3.6.1'){
		sh 'mvn package'
		}
	}
}
