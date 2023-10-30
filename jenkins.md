**1.in jenkins pippeline, it have 10 stages and in 5th stage sucessfully run automatically shows result stage 7.     
Answer:**     

**2.Jenkins pipeline, we have 10 stages in the stage 5 is failed but we need pass to stage 4 to stage 6.   
Answer:** We can configure your pipeline to continue running stages even if a particular stage fails. To allow a Jenkins pipeline to proceed from stage 4 to stage 6 even when stage 5 fails, you can use the catchError or try...catch approac      
pipeline {
    agent any
    stages {
        stage('Stage 4') {
            steps {
                // Stage 4 steps here
            }
        }
        stage('Stage 5') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    // Stage 5 steps here
                }
            }
        }
        stage('Stage 6') {
            steps {
                // Stage 6 steps here
            }
        }
    }
}

    
**3.mvn clean install vs mvn clean deploy   
Answer:** mvn clean install and mvn clean deploy are Maven commands used in software development.    
mvn clean install compiles the project, runs tests, and installs the project's artifacts (usually JAR files) in the local Maven repository. It's commonly used during development and testing phases to make the project's artifacts available for other local projects that depend on them.    
mvn clean deploy goes a step further, deploying the project's artifacts to a remote repository, typically a company-wide or public repository like Maven Central. This is typically done when the project is considered stable and ready for use by other developers and projects. It's an important step in sharing and distributing software libraries.    

**4.mvn stages
Answer:**    
**5.jenkins shared library   
Answer:** A Jenkins Shared Library is a reusable collection of Groovy code and resources that enables organizations to centralize and standardize their Jenkins pipeline logic. It serves as a way to share common functions, steps, and best practices across multiple Jenkins pipelines. By defining and maintaining shared libraries, teams can improve code quality, reduce duplication, and simplify pipeline management. These libraries are typically stored in version control repositories, making it easy to update and share changes across Jenkins pipelines. Jenkins Shared Libraries promote collaboration and consistency in Continuous Integration and Continuous Delivery (CI/CD) processes, ultimately streamlining the development and automation of software projects.    

**6. in production ,if plugins are installed and the process need to safe restart in production   
Answer:**    

**7.Why we need multi branch pipeline?    
Answer**    Multi-branch pipelines in Jenkins provide significant benefits for organizations and development teams, primarily for managing and automating Continuous Integration (CI) and Continuous Delivery (CD) workflows in software development. These pipelines are designed to work with repositories containing multiple branches and pull requests.    
Automated Branch Management,    Efficient Resource Utilization,    Parallel Processing,    Easy Scalability,    Branch Isolation,    Comprehensive Testing     
**8.How can you copy job from your local jenkins instance to other local jenkins instance?   
Answer** https://wiki.jenkins-ci.org/display/JENKINS/Administering+Jenkins     

**9.Can you list few ways by which we can trigger our build in Jenkins? What is the difference between Build Periodically and Poll SCM?   
Answer** Build Periodically:     
It triggers builds at specific times or on a regular schedule defined using a cron-like syntax.     
Useful for running builds at predetermined intervals, such as nightly builds, weekly builds, etc.     
Builds are initiated even if there are no code changes, which can lead to unnecessary builds.     
Poll SCM:     
It periodically checks the version control system (e.g., Git, SVN) for code changes and triggers a build when changes are detected.     
Useful when you want builds to be triggered only when there are code changes, reducing unnecessary build runs.     
It's more efficient than "Build Periodically" in terms of resource usage, as it doesn't trigger builds unless there are changes.     

**10.What are multi branch pipeline?   
Answer** https://devopscube.com/jenkins-multibranch-pipeline-tutorial/     
**11.What are active and reactive parameters (Dynamic parameterization) in Jenkins ?   
Answer**Active Choices Parameter:    
An Active Choices parameter dynamically generates a list of value options for a build parameter using a Groovy script or a script from the Scriptler catalog.
Active Choices Reactive Parameter:    
An Active Choices Reactive Parameter can generate the same set of value options as the Active choice parameter; in addition to that, it can be dynamically updated with the values based on the selection in some other build parameter that was referred to in the Active choices reactive parameter.

**12.How to set Jenkins build to fail based specific word in console output ?   
Answer**We can set up Jenkins to fail a build based on a specific word or phrase in the console output using the "Text Finder" or "Text Finder Post-Processor" plugin    You can either create a new Jenkins job or modify an existing one. In your job configuration, make sure you have the necessary build steps configured, and you are capturing the console output.    
To fail the build based on specific text in the console output, add a post-build action to your job:
In the job configuration, scroll down to the "Post-build Actions" section.
Click on "Add post-build action" and select "Text Finder" or "Text Finder Post-Processor" depending on which one you've installed.    

**13.what is the need of CICD tools?   
Answer**
**14.What type of Jenkinsfile you have worked on?   
Answer** Declarative Jenkinsfile: This is a simplified way of defining Jenkins pipelines. It uses a more structured and less code-heavy syntax. Declarative Jenkinsfiles are well-suited for straightforward, linear pipelines and are easier for beginners to understand.    

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
