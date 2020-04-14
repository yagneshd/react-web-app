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
