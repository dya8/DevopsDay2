pipeline
{
    agent any
    stage('Checkout')
    {
        steps
        {
            echo 'Fetching source code'
            checkout scm
        }
    }

  stage('Code Quality Check!')
    {
        steps
        {
            echo 'Checking code quality.'
            bat '''
            findstr GOOD quality.txt >nul
            if errorlevel1
            (
            echo Code Quality Failed
            exit 1
        )
        else
        (
          echo Code Quality Passed
        )
        '''
    }
    }
    stage('Generate Report')
    {
        steps
        {
            echo 'Generating built report'
            bat '''
            mkdir reports
            echo Build Successful > reports \\build-report.txt
            '''
            
        }
    }

    stage('Archive Artifacts')
    {
        steps
        {
            echo 'Archiving reports'
            archveArtifacts artifacts: 'reports/*txt', fingerprint:true
    stage('Deploy')
    {
        steps
        {
            echo 'Deploying the application'
        }
       
    }
}
