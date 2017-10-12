pipeline  {
    agent any
   stages {
        stage('connect') {
            steps {
                echo 'checkout..'
                checkout([$class: 'SubversionSCM', additionalCredentials: [], excludedCommitMessages: '', excludedRegions: '', excludedRevprop: '', excludedUsers: '', filterChangelog: false, ignoreDirPropChanges: false, includedRegions: '', locations: [[credentialsId: '749ca61b-c86d-4467-888f-a6bbc22dc3d5', depthOption: 'infinity', ignoreExternalsOption: false, local: '.sources', remote: 'svn://dvsvffm/prod/se/xsta/sources/berlinpayment-connector/trunk']], workspaceUpdater: [$class: 'UpdateWithRevertUpdater']])
            }
        }
        stage('berlinpayment-connector') {
            steps {
                build job: 'berlinpayment-connector', quietPeriod: 1
            }
        }
        stage('berlinpayment-connector-test') {
            steps {
                build job: 'berlinpayment-connector-tests', quietPeriod: 1
            }
        }
        stage('tooling') {
            steps {
                checkout([$class: 'SubversionSCM', additionalCredentials: [], excludedCommitMessages: '', excludedRegions: '', excludedRevprop: '', excludedUsers: '', filterChangelog: false, ignoreDirPropChanges: false, includedRegions: '', locations: [[credentialsId: '749ca61b-c86d-4467-888f-a6bbc22dc3d5', depthOption: 'infinity', ignoreExternalsOption: false, local: 'tooling', remote: 'svn://dvsvffm/prod/se/autista/build/hudson-build-tools/trunk']], workspaceUpdater: [$class: 'UpdateWithRevertUpdater']])
            }
        }
        stage('epay21') {
            steps {
                checkout([$class: 'SubversionSCM', additionalCredentials: [], excludedCommitMessages: '', excludedRegions: '', excludedRevprop: '', excludedUsers: '', filterChangelog: false, ignoreDirPropChanges: false, includedRegions: '', locations: [[credentialsId: '749ca61b-c86d-4467-888f-a6bbc22dc3d5', depthOption: 'infinity', ignoreExternalsOption: false, local: 'epay21-connector/sources', remote: 'svn://dvsvffm/prod/se/xsta/sources/epay21-connector/trunk']], workspaceUpdater: [$class: 'UpdateWithRevertUpdater']])
            }
        }
   }
}