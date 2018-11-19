# REST API Example with Wildfly for BEC LSD Openshift demo.

http://localhost:8080/RESTExample/

In the /api/ you find the root path where all the API is located for all the services.
For now there's only one service, that is the purchase simulation:
http://localhost:8080/RESTExample/api/

The service for the purchase simulation is in the /api/decision/
So far there's only two operations supported: GET and POST.

GET on the main path of /api/purchase/ will return all the users.

GET on a concrete user will return the current balance of that user: RESTExample/api/purchase?email=jkrochmalski@gmail.com

POST : add a new purchase for a new user that will be identified by its email. It expects a JSON object
with the following format:
{"email":"jr@gmail.com","first_name":"John","last_name":"Rambo","amount":300}



##create application on Openshift:

    oc new-app wildfly:13.0~https://github.com/jotka/rest-example-lsd.git

    oc logs -f bc/rest-example-lsd
    
    oc get builds
    
    oc get services
    
    oc expose svc/rest-example-lsd 
    
    oc get routes

http://rest-example-lsd-myproject.127.0.0.1.nip.io

http://rest-example-lsd-myproject.127.0.0.1.nip.io/RESTExample/

http://rest-example-lsd-myproject.127.0.0.1.nip.io/RESTExample/api/

http://rest-example-lsd-myproject.127.0.0.1.nip.io/RESTExample/api/purchase/