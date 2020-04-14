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
								gsutil cp * gs://artifactory-server/
								'''
								
							 }
                           }
						  
						  
                        }
                   }
				 }  
              
