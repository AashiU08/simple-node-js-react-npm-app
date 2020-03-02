
def notify(status){
    emailext (
       body: """<p> Jenkins Pipeline Notification </p>
            <table border="1" cellpadding="0" cellspacing="0" style="">
                <thead>
                    <tr style=" background:#000; color:#ffffff;text-align:center ">
                        <th colspan="2" style="padding: 4px;"> PipeLine Job Notification </th>
                    
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td style="padding: 4px;">Job Name</td>
                        <td style="padding: 4px;">${env.JOB_NAME}</td>
                    </tr>
            <tr>
                        <td style="padding: 4px;">Job Status</td>
                        <td style="padding: 4px;">${status}</td>
                    </tr>
            <tr>
                        <td style="padding: 4px;">Build Number</td>
                        <td style="padding: 4px;">${env.BUILD_NUMBER}</td>
                    </tr>
            <tr>
                        <td style="padding: 4px;">Build URL</td>
                        <td style="padding: 4px;"><a href="${env.BUILD_URL}"> ${env.BUILD_URL} </a> </td>
                    </tr>
            <tr>
                        <td style="padding: 4px;">Notification sent by </td>
                        <td style="padding: 4px;">Aashi Upadhyay</td>
                    </tr>
                </tbody>
                <tfoot>
                    <tr>
                        <td colspan="2" style="padding: 4px;">This is an auto-generated email and reply to this mail id is not monitored. In case of any query please contact [snigdhaupadhyay08@gmail.com]</td>
                        
                    </tr>
                </tfoot>
            </table>
            """,
       subject: """JenkinsNotification: ${status}:""", 
       to: 'aashi.upadhyay@assetvantage.com'
           )
}
pipeline {
    agent {
        docker {
            image 'node:7-alpine'
            args '-p 3000:3000'
        }
    }
    environment { 
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'

                notify ('npm has been installed')
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'

                notify ('test stage has been executed')
            }
        }
        stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                sh './jenkins/scripts/kill.sh' 
            }
        }
    }
}