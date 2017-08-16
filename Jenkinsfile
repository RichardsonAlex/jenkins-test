def targets = ['cheri256', 'cheri128']
def jobs = [:]
for (x in targets) {
    def label = x // Need to bind the label variable before the closure - can't do 'for (label in labels)'

    // Create a map to pass in to the 'parallel' step so we can fire all the builds at once
    jobs[label] = {
      node('docker') {
        // build steps that should happen on all nodes go here
        def sdkImage = docker.image("ctsrd/cheri-sdk-${label}:latest")
        sdkImage.pull() // make sure we have the latest available from Docker Hub
        stage("build ${label}") {
          sdkImage.inside {
            sh 'echo Running in SDK image && clang -v'
          }
        }
        stage("test ${label}") {
          ansiColor('xterm') {
            // Just some echoes to show the ANSI color.
            sh "\u001B[31mI'm Red\u001B[0m Now not"
          }
        }
      }
    }
}

parallel jobs
