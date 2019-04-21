pipeline {

    agent any
    // agent {
    //     docker {
    //         image 'node:6-alpine' 
    //         args '-p 3000:3000' 
    //     }
    // }
    
    environment {
        PATH='/usr/local/bin:/usr/bin:/bin'
	}

    stages {

        // stage('npm-build') {
        //     agent {
        //         docker {
        //             image 'node:7.4'
        //         }
        //     }
        
        //     steps {
        //         echo "Branch is ${env.BRANCH_NAME}..."
        
        //         withNPM(npmrcConfig:'my-custom-npmrc') {
        //             echo "Performing npm build..."
        //             sh 'npm install'
        //         }
        //     }
        // }

       stage('NPM Setup') {
          steps {
             sh 'npm install'
         }
       }

       stage('IOS Build') {
          steps {
             sh 'ionic cordova build ios --release'
             
          }
       }

       stage('Android Build') {
          steps {
               sh 'ionic cordova build android --release'
               
          }
       }

       stage('APK Sign') {
          steps {
            // sh 'jarsigner -storepass your_password -keystore keys/yourkey.keystore platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk nameApp'
              echo "Android"
          }
       }



      stage('Stage Web Build') {
          steps {
              sh 'npm run build --prod'
          }
       }

         stage('Publish Firebase Web') {
          steps {
              //sh 'firebase deploy --token "YourTokenKey"'
              echo 'Firebase Deploy'
          }
       }

        stage('Publish iOS') {
          steps {   
              echo "Publish iOS"
          }
       }

        stage('Publish Android') {
          steps {
              echo "Publish Android"
          }
       }


}
}

