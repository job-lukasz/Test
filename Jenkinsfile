@Library('stackLibrary@promotion')
import com.silvair.jenkinsci.GitWrapper
import com.silvair.jenkinsci.Helpers.LogLevel;
import com.silvair.jenkinsci.Helpers.JSONWriter;

@NonCPS
int sorter(a,b){ 
    return stringComparator(a.name,b.name);
}

pipeline {
    agent {label 'master'};
    environment {
        STATUSES="{}"
    }
    options {
        skipDefaultCheckout();
    }
    parameters {
        string(name: 'TEST_BRANCH', defaultValue: 'dev', description: 'Branch to execute pipeline')
    }
    stages {
    // lock(label: 'meshroomBuild'){
    //     stage("Preparations"){
    //         steps {
    //             script{
    //                 vars.readFromFile(this);
    //             }
    //         }
    //     }
     stage("Preparation"){
           steps {
                    script{
                        vars['testBranch'] = params.TEST_BRANCH
                        def testCodeGit = new GitWrapper(this, "https://github.com/job-lukasz/test.git", vars['testBranch'], "", false)
                        try {
                            testCodeGit.pull();
                        } catch (error) {
                            vars['testBranch'] = "master";
                            testCodeGit = new GitWrapper(this, "https://github.com/job-lukasz/test.git", vars['testBranch'], "", false)
                            testCodeGit.pull();
                        }
                        currentBuild.displayName = "#${env.BUILD_NUMBER} [${params.TEST_BRANCH}]"
                    }
                // emailext(to: "lukasz.job@silvair.com",
                //         subject: "[Jenkins] ${env.JOB_NAME} ${env.BUILD_DISPLAY_NAME} '${currentBuild.currentResult}'",
                //         mimeType: 'text/html',
                //         body: """
                //             <span style="font-family:sans-serif;font-size:1em;">
                //             This job was triggered by Master job build:<br>
                //             Build ${env.JOB_NAME} build: ${env.BUILD_DISPLAY_NAME} finished with status "${currentBuild.currentResult}"<br>
                //             New version of production firmware was sent to S3 bucket: silvair-fw-app-prod<br>
                //             </span>
                //             """//,
                //         //attachmentsPattern: "${dfuimgName}"
                // )
                // script{
                //     dir("someDir"){
                //         sh("""
                //             rm -rf localDir
                //             mkdir localDir
                //             mkdir localDir/test
                //             touch localDir/test/FileToUpload0
                //             touch fileNotToUpload
                //             touch localDir/FileToUpload1
                //             touch localDir/FileNotToUpload1
                //             touch ../FileToUpload2
                //         """)
                //     }
                //     promote.init(this, false, "feature", "1000", "test")
                //     promote.toBronze(["someDir/localDir/test/FileToUpload*", "someDir/localDir/FileTo*","FileTo*"])
                //     promote.toSilver()
                //     promote.toGold()
                //     promote.toPlatinum()
                // }
                // ws("workspace/Master-Smoke-nRF5x-DimmingModule/fw/project/_bin/"){
                //     script{
                //         def _bucket = "silvair-fw-app-ci"
                //         def _path = "DimmingPWM/${env.BUILD_NUMBER}/"
                //         def files = [
                //                 'FW-MESH-nRF5x-DimmingModule_debug_SUPERHEX.hex', '*debug.hex', '*debug*dfuimg.zip',
                //                 '*release*SUPERHEX*hex', '*release*dfuimg*', '..\\_variants\\_bin\\*als_adc.hex',
                //                 '..\\_variants\\_bin\\*als_bh1726.hex', '..\\_variants\\_bin\\*244*hex',
                //                 '..\\_variants\\_bin\\*977*hex', '..\\_variants\\_bin\\*1953*hex',
                //                 '..\\_variants\\_bin\\*7816*hex', '..\\_variants\\_bin\\*31311*hex'
                //         ]
                //         withAWS(credentials:'s3-credentials', region: 'eu-central-1') {
                //             for (_file in files) {
                //                 def path = bat(script: "@dir /b /s ${_file}", returnStdout: true).trim()
                //                 echo path
                //                 def fullName = path.replaceAll('C:\\\\Jenkins\\\\workspace\\\\Master-Smoke-nRF5x-DimmingModule\\\\fw\\\\project\\\\_bin\\\\','')
                //                 echo fullName
                //                 s3Upload(file: fullName, bucket: _bucket, path:_path)
                //             }
                //         }
                //     }
                // }
            }
        }
        stage("CheckSCMChanges"){
            steps {
                script{
                    // def wrapper = new GitWrapper(this,"https://github.com/homersoft/FW-MESH-nRF5x-DimmingModule.git", "dev")
                    // def sha = wrapper.getRemoteCommitSha();
                    // echo sha
                    //  withAWS(credentials: 's3-meshrooms', region: 'us-east-1') {
                    //         def folder = 'rc'
                    //         def files = s3FindFiles(bucket: 'silvair-fw-core', path: folder);
                    //         vars["version"] = files.max(this.&sorter).name;
                    //         echo vars["version"];
                    //     }
                    // stagesStatuses["Build"] = "SUCCESS";
                    // stagesStatuses["Deploy"] = "Failure";
                    // if(stagesStatuses["Build"] == "SUCCESS"){
                    //     echo "sdfdfgsdf"
                    // }
                    // def tmp = stagesStatuses.serialize()
                    // echo tmp;
                    // stagesStatuses.deserialize(this, tmp);
                    // echo stagesStatuses["Build"];
                }
            }
        }
        stage("Build"){
            steps {
                script{
                    
                }
            }
        }
        stage("Smoke Tests"){
            steps {
                script{
                }
            }
        }
        stage("Component Tests"){
            steps {
                script{
                }
            }
        }
    }
    post {
        always {
            script{
            }
            echo "Tasks finish"
        }
    }
}
