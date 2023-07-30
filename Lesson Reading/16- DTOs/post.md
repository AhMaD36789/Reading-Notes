# DTOs

what:

Data Transfer Objects are simple object thats used to transfer data between different layers of an application

why:

- Privacy and security
- Speed and effeciency
- Seperation of concerns

how:

create new folder inside Models called DTO

create new class naming scheme(...DTO)

include any properties that i want the DTO to read from server and get back to the client with it in the DTO class

change the interfaces to pull data from DTO

change service to include DTO

change the code thats dealing with entity object
