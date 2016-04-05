# Egg API: an simple api for nodejs
Egg API is a simple api rule for http based api design.   
Egg API is to reduce complexity Restful Api introduced.

1. Egg API uses HTTP GET/POST as the primary methods.
2. GET mehtod for Data retrieving from server.
3. POST method for Data sending to server.
4. Any API using GET method will not change any data of the user.
5. Any API using POST method will change the state, info or data of the user.
6. All APIs using GET method will start with a noun, like user/admin.  
  * simply a noun indicates that you want to retrieve all data  
    > GET /user  
  * default page limit is 20, if you want to change this limit, specify a value to limit, limit is only valid here.  
    > GET /user?limit=50  
  * default page number is 1, if you want to change page number, specify a value to page.  
    > GET /user?page=5  
  * page & limit can be combined as get parameter 
    > GET /user?page=5&limit=50  
  * followed a number or id to get a single item, limit will have no effect here, and be ignored.  
    > GET /user/1  
    > GET /user/1?limit=50 

7. All api using POST method must start with a verb, like create/update/remove which will change something, but not get/list/show which will not make can changes.
    a simple example will be:
    > POST /create/user  
    > POST /update/user  
    > POST /remove/user  

8. POST format should be in accordance with form post. Should never post a json/xml files as the parameter container.
     > POST /create/user
     > ...
     > 
     > 
     > name=aaa&password=asdfsf
9. All APIs return json only.
10. return json should at lease have the following fields:

    | field name | Description |
    | --- | --- |
    | code | error code|
    | message | error message|
    | data | return data |

11. Error code is primarily defined by [errorable](https://github.com/calidion/errorable) and it's library [common](https://github.com/Errorable/common).
