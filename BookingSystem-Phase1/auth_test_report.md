This document is used as a report of a pentesting for the autorizations of the booking system.


Guests :
Can :
- Access the registration page '/register'
- Register as a reserver
- Register as an administrator ❌Bug, To register as an administrator, you should have an authorization.
- Access the login page '/login'
- Access the resources page '/resources' ❌Bug, specs says only a registered user can
- Add a resource '/resource' ❌Bug, specs says only a registered user can
- See the reservations 'home'
- View all resources, reservations and users via API endpoints '/api/resources', '/api/reservations', '/api/users' ❌bug, Endpoints should not be visible


Cannot :
- Access the reservation page '/reservation'
- Add, Delete or update a reservation
- Delete or update a resource
- Register if is less than 15 years old '/register'
- Register with an invalid email or password '/register'
- See the name of the reserver 'home'
- Add, delete or modify a ressource, reservation or user via the APIs endpoints

Reserver :
Can :
- Logout 'home'
- Access the reservation page '/reservation'
- Add a reservation '/reservation'
- Delete or update its own reservation '/reservation'
- Make a reservation at the same resource and time as another ❌bug, the specs says that it is hourly reserved
- Update everyones reservations ❌bug, accessible by putting '/reservation?id='number'
- Access the resources page by pressing on the button '/resources' ❌bug, only administrator should
- Add a resource '/resources' ❌bug, only administrator should had the possibility
- Delete or update everyones resource ❌bug, accessible by putting '/resources?id='number''
- See the name of the reservers 'home'
- Reserve with the name of another person ❌bug, should be able to only reserve with its own name. Doable by modifying your own reservation (or another one with the IDOR bug)
- View all resources, reservations and users via API endpoints '/api/resources', '/api/reservations', '/api/users' ❌bug, Endpoints should not be visible
- Register ❌bug, should not be able to register if already logged in. Accessible by putting '/register' at the end of the url
- Log in❌bug, should not be able to login if already logged in. Accessible by putting '/login' at the end of the url
- 

Cannot :
- Delete everyones reservations
- Delete its own account

Administrator :
Can :
- Logout 'home'
- Access the reservation page '/reservation'
- Add a reservation '/reservation'
- Update or delete everyone's reservations '/reservation'
- Access the resources page '/resources'
- Add a resource '/resources'
- Update or delete everyone's resources by putting '?id='number' at the end of the reservation url ❌bug, should be able to do it in an easier way
- Make a reservation at the same resource and time as another ❌bug, the specs says that it is hourly reserved
- See the name of the reserver 'home'
- Reserve with the name of another person ❌bug, this is an identity thief, illegal even for an admin
- Register ❌bug, should not be able to register if already logged in. Accessible by putting '/register' at the end of the url
- Log in❌bug, should not be able to login if already logged in. Accessible by putting '/login' at the end of the url
- View all resources, reservations and users via API endpoints '/api/resources', '/api/reservations', '/api/users'

Cannot :
- Delete a user account (at least I did not find how) ❌bug, the specs says it should be possible for an admin to do so
