pipeline{

agent{label 'linux'}
    stages{
		stage('Test'){
			steps{
				sh 'ant -f test.xml -v'
				junit 'reports/*.xml'
			}
		}
	        stage('Build')	{
			steps{
				sh 'ant -f build.xml -v'
			}
		}
	    	stage('Deploy') {
		        steps{
				withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', 
                 		     accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
					sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-*.jar s3://mish0020asgn9/'
				}
			}
    		}
	}
}
