pipeline {
    agent {label 'linuxSlave'}
        stages{
            stage('buildAll'){
                when{
                    expression{
                        params.LANGUAGE == "all"
                    }
                }
                steps{
                    sh '''
                        echo "You choosed to run all scripts.."
                        cd ~/Documents/scripts
                        ls
                        echo "Now the bash script"
                        bash bashsc.sh
                        echo "Now the python script"
                        python3 pysc.py
                    '''
                }
            }
            
            stage('buildBash'){
                when{
                    expression{
                        params.LANGUAGE == "bash"
                    }
                }
                steps{
                     sh '''
                        cd ~/Documents/scripts
                        ls
                        bash bashsc.sh
                    '''
                }
            }
            
            stage('buildPy'){
                when{
                    expression{
                        params.LANGUAGE == "python"
                    }
                }
                steps{
                    sh '''
                        cd ~/Documents/scripts
                        ls
                        python3 pysc.py
                    '''
                }
            }
            
            stage('buildC'){
                when{
                    expression{
                        params.LANGUAGE == "c"
                    }
                }
                steps{
                    echo 'run c scripts'
                }
            }
            stage('Saving results') {
                steps{
                    echo 'Saving results'
                    sh '''
                        
                        mkdir -p ${HOME}/workspace/ProjectJenk
                        cd ${HOME}/workspace/ProjectJenk
                        if [-f "result_file.txt"]; then
                            echo "File exists."
                        else
                            touch result_file.txt
                        fi    
                            date >> result_file.txt
                            echo "USER=$USER JOB_NAME=$JOB_NAME" >> result_file.txt
                            echo "Build number $BUILD_NUMBER" >> result_file.txt
                            echo "*********************" >> result_file.txt
                    '''
                }
            }
        }
    
}
