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
							 ls -ltr
							 npm install
							 npm run build
							 cd build
							 tar -cvf "frontend-${BUILD_NUMBER}.tar *
							    '''
							 
                            }
                          }
						  
						  stage('Deploy') 
                          {
                           steps 
                            {
                             							 
                             sh '''
								ls -ltr
								cd build
								tar -xvf "frontend-${BUILD_NUMBER}.tar
								ls -ltr		
							    '''
							 
                            }
                          }
						  
						  
                        }
                   }
