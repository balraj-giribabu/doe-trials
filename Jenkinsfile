pipeline{
    agent any
    stages{
        
        stage("verifying changes"){
            steps{
                
                script{
                    List<String> changedFiles = changes_method()
                    println "changed files list"
                    println changedFiles
                    
                    for (item in changedFiles){
                        if(item=="package.json"){
                            println "perform npm install and other 3 cmds"
                        }
                        else{
                            println "perform other 3 commands only"
                        }
                    }
                }
            }
        }
    }
}

@NonCPS

List<String> changes_method(){
    def changedFiles_2 = []
    def changeLogSets = currentBuild.changeSets
    for (entries in changeLogSets) {
        for (entry in entries) {
            for (file in entry.affectedFiles) {
                echo "Found changed file: ${file.path}"
                changedFiles_2 += "${file.path}"
             }
        }
    }
    print changedFiles_2
    return changedFiles_2
}
