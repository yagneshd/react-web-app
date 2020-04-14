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
						  
						  stage('Deploy') 
                          {
                           steps 
                            {
							
							 script
							  {	
                             							 
                             sh '''
								cd build
								tar -xvf frontend-${BUILD_NUMBER}.tar
								rm -rf frontend-${BUILD_NUMBER}.tar
								ls -ltr
								gsutil acl ch -u AllUsers:R gs://test-vijayg
								gsutil defacl set public-read gs://test-vijayg
								gsutil web set -m index.html -e index.html gs://test-vijayg
								gsutil cp -r * gs://test-vijayg/
								gsutil setmeta -h "content-type: image/svg+xml" gs://test-vijayg/static/media/*.svg
								'''
								
							 }
                           }
						  
						  
                        }
                   }
				 }  
              
