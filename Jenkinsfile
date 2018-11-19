pipeline{

agent{label 'linux'}
    stages{
		stage('Test'){
			steps{
				sh 'ant -f test.xml -v'
				sh 'junit reports/*.xml'
			}
		}	
    }
}
