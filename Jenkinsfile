pipeline
  {
	  agent { label 'master' }
stages{
	
    stage('Checkout')
	{
		steps
		{
			cleanWs()
		 	checkout scm
			echo "hello dotnet"
   			println 'hello world'
		}
	}
    stage('Build Solution')
	{
		steps
		{
		 //powershell 'dotnet clean'
		 powershell 'DemoDotNETCoreApplication.sln /Clean'
		 powershell 'dotnet --version'
		 
		 //powershell 'dotnet build'
		}
	}
 stage('Appl deploy on deployment server')
        {
            steps
            {
                sshagent(['12345']) {
			powershell 'ssh msagad/ladmin@10.128.17.30 "mkdir demo"'
		}
	    }
	}

	
    /*stage('Unit Testing and Code Coverage')
		{
		steps
		  {
			powershell 'C:/Users/mukeshjoshi/AppData/Local/Apps/OpenCover/OpenCover.Console.exe -target:"dotnet.exe" -output:coverage.xml -filter:"+[DemoDotNETCoreApplication*]* -[*.Tests*]*" -targetargs:"test" -register:user -oldstyle'
		  }
		}

	stage ('SonarQube Analysis')
      	{
         steps
		 {
			 withSonarQubeEnv('SonarQube')
			 {
			  powershell '''
			  dotnet C:/Users/mukeshjoshi/Desktop/sonar-scanner-msbuild-4.6.0.1930-netcoreapp2.0/SonarScanner.MSBuild.dll begin /k:"dotnetcoreproject" /d:sonar.cs.opencover.reportsPaths="coverage.xml"
			  dotnet build DemoDotNETCoreApplication.sln
			  dotnet C:/Users/mukeshjoshi/Desktop/sonar-scanner-msbuild-4.6.0.1930-netcoreapp2.0/SonarScanner.MSBuild.dll end
			  '''
			 } 
		 }	
      	}
	*/	
	
      }
  }
