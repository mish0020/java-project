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
			sh 'ant -f build.xml -v'
		}
    }
}
