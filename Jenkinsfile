                  pipeline 
                   {
                       agent any    
                       tools
                       {
                           
                           nodejs  'node'

                       }
                       stages 
                        {
                          stage('Build') 
                          {
                           steps 
                            {
                              script
							{   
							   checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github_credential', url: 'https://github.com/vmgponly/react-web-app.git']]]
                             
							 sh '''
                             node --version
                             npm --version
                             
                             npm install
                             npm run build
                             ls -ltr
                             cd build/
                             tar -cvf frontend-${BUILD_NUMBER}.tar *
                             '''
                           }   
                            }
                          }
                           stage('Deploy') 
                          {
                           steps 
                            {

                                sh '''
                                cd build
                                tar -xvf frontend-${BUILD_NUMBER}.tar
                                rm -rf frontend-${BUILD_NUMBER}.tar
                                ls -ltr
                                gsutil acl ch -u AllUsers:R gs://test-bucket
                                gsutil defacl set public-read gs://test-bucket
                                gsutil web set -m index.html -e index.html gs://test-bucket
                                gsutil cp -r * gs://test-bucket/
                                gsutil setmeta -h "content-type: image/svg+xml" gs://test-bucket/static/media/*.svg
                                '''
                             
                            }
                          }
                     }
                  }
