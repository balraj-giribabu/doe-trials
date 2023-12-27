pipeline{
    agent any
    stages{
        
        stage("Verifying"){
            steps{
                
                script{
                    List<String> changedFiles = changes_method()
                    def package_json_updated = false
                    println "changed files list"
                    println changedFiles
                    
                    for (item in changedFiles){
                        if(item=="package.json"){
                            package_json_updated = true
                        }
                    }
                    
                    stage("Deploying"){
                        if(package_json_updated){
                            bat """
                            mkdir test-dir1
                            mkdir test-dir2
                            rmdir test-dir1 /s /q
                            rmdir test-dir2 /s /q
                            """
                            println package_json_updated
                        }
                        else{
                            println "perform other 3 commands only"
                            println package_json_updated
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
    return changedFiles_2
}
