Pipeline{
	any agent{
		Stages{
			stage('any text scm Checkout'){
			git 'https://github.com/sumeetmoralwar/maven-project.git'}
			
			stage('test source code'){
				steps{
					withMaven(maven: 'LocalMaven'){
					sh 'mvn test'
					}
				      }
			 }	

			stage('create package'){
				steps{
					withMaven(maven: 'LocalMaven'){
					sh 'mvn package'
					}
				}
			}

			stage('install package'){
				steps{
					withMaven(maven: 'LocalMaven'){
					sh 'mvn install'
					}
				}
			}
		}
	}
}
