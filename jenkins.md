**1.in jenkins pippeline, it have 10 stages and in 5th stage sucessfully run automatically shows result stage 7.     
Answer:**     

**2.Jenkins pipeline, we have 10 stages in the stage 5 is failed but we need pass to stage 4 to stage 6.   
Answer:**   
**3.mvn clean install vs mvn clean deploy   
Answer:**
**4.mvn stages
Answer:**
**5.jenkins shared library   
Answer:**
**6. in production ,if plugins are installed and the process doesn't restart in production   
Answer:**
**7.Why we need multi branch pipeline? 8.How can you copy job from your local jenkins instance to other local jenkins instance?   
Answer**
**9.Can you list few ways by which we can trigger our build in Jenkins? What is the difference between Build Periodically and Poll SCM?   
Answer**
**10.What are multi branch pipeline?   
Answer**
**11.What are active and reactive parameters (Dynamic parameterization) in Jenkins ?   
Answer**
**12.How to set Jenkins build to fail based specific word in console output ?   
Answer**
**13.what is the need of CICD tools?   
Answer**
**14.What type of Jenkinsfile you have worked on?   
Answer**
**15.Can we have job for pr and once merge is done the source branch should be deleted?   
Answer**Yes, you can set up a Jenkins job to perform tasks like PR (Pull Request) validation and branch deletion once the merge is done. To achieve this, you will need to use a combination of Jenkins plugins and pipeline scripting.    
Install Required Plugins:GitHub Integration Plugin,Pipeline Plugin   
pipeline {    
    agent any    
    stages {    
        stage('Checkout') {    
            steps {    
                // Checkout the code from the PR branch    
                checkout([$class: 'GitSCM', branches: [[name: 'origin/${CHANGE_BRANCH}']], userRemoteConfigs: [[url: 'https://github.com/your/repo.git']]])
            }    
        }    
        stage('PR Validation') {    
            steps {    
                // Add steps for PR validation (e.g., build, test, and other checks)    
            }    
        }    
        stage('Merge and Delete') {    
            when {    
                // This stage will run only if the PR is merged    
                expression { currentBuild.rawBuild.resultIsBetterOrEqualTo('SUCCESS') }    
            }    
            steps {    
                // Merge the PR (e.g., using GitHub API or git command)    
                // Delete the source branch    
            }    
        }    
    }    
}    
When a PR is created or updated in your GitHub repository, the webhook will trigger the Jenkins job. If the PR validation is successful, the "Merge and Delete" stage will execute, merging the PR and deleting the source branch.  
