pipeline  {
    agent any
   stages {
        stage('connect') {
            steps {
                echo '## CHECKOUT ##'
                checkout([$class: 'SubversionSCM', additionalCredentials: [], excludedCommitMessages: '', excludedRegions: '', excludedRevprop: '', excludedUsers: '', filterChangelog: false, ignoreDirPropChanges: false, includedRegions: '', locations: [[credentialsId: '749ca61b-c86d-4467-888f-a6bbc22dc3d5', depthOption: 'infinity', ignoreExternalsOption: false, local: '.sources', remote: 'svn://dvsvffm/prod/se/xsta/sources/berlinpayment-connector/trunk']], workspaceUpdater: [$class: 'UpdateWithRevertUpdater']])
            }
        }
        stage('build: berlinpayment-connector') {
            steps {
                 echo '## BUILD berlinpayment-connector ##'
                build job: 'berlinpayment-connector', quietPeriod: 1
            }
        }
        stage('build: berlinpayment-connector-test') {
            steps {
                echo '## BUILD berlinpayment-connector-testS ##'
                build job: 'berlinpayment-connector-tests', quietPeriod: 1
            }
        }
        stage('checkout: tooling') {
            steps {
                echo '## CHECKOUT hudson-build-tools ##'
                checkout([$class: 'SubversionSCM', additionalCredentials: [], excludedCommitMessages: '', excludedRegions: '', excludedRevprop: '', excludedUsers: '', filterChangelog: false, ignoreDirPropChanges: false, includedRegions: '', locations: [[credentialsId: '749ca61b-c86d-4467-888f-a6bbc22dc3d5', depthOption: 'infinity', ignoreExternalsOption: false, local: 'tooling', remote: 'svn://dvsvffm/prod/se/autista/build/hudson-build-tools/trunk']], workspaceUpdater: [$class: 'UpdateWithRevertUpdater']])
            }
        }
        stage('build: epay21 connector') {
            steps {
                echo '## CHECKOUT epay21-connector ##'
                checkout([$class: 'SubversionSCM', additionalCredentials: [], excludedCommitMessages: '', excludedRegions: '', excludedRevprop: '', excludedUsers: '', filterChangelog: false, ignoreDirPropChanges: false, includedRegions: '', locations: [[credentialsId: '749ca61b-c86d-4467-888f-a6bbc22dc3d5', depthOption: 'infinity', ignoreExternalsOption: false, local: 'epay21-connector/sources', remote: 'svn://dvsvffm/prod/se/xsta/sources/epay21-connector/trunk']], workspaceUpdater: [$class: 'UpdateWithRevertUpdater']])
 				withAnt(installation: 'Ant', jdk: 'Java') {
   					       bat "ant dist"
				}
       
            }
        }
   }
}