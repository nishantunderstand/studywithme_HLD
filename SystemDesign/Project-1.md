My Microservice Architecture :

Incoming Request
API Gateway By AWS
LoadBalancer : Master-Slave 
SecurityFilterChain
	UserNameFiletChain
		JWT Token Authenticate
			Store in UserSecurityContext
		
DispatcherServlet
	HandlerMapper
		Controller 
			Facade
				Service, Repository, Entity, Tranformer
					DB
				Resposnse Return
				