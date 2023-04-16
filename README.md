```
Spring Sagas

Use Case:

when an user places an order, order will be fulfilled if the product's price is within
the user's credit limit/balance. Otherwise it will not be fulfilled.
```

<img width="1318" alt="Screenshot 2023-04-16 at 12 53 33 PM" src="https://user-images.githubusercontent.com/43849911/232280236-3932575f-a2b6-4488-af5f-4289dc2df606.png">

```
In the above pic, both the applications are pointing to the single database as the system is monolithic 
and can be considered as a single transaction.
```

<img width="1083" alt="Screenshot 2023-04-16 at 12 56 56 PM" src="https://user-images.githubusercontent.com/43849911/232280404-2d67d05a-d690-44d4-9ee2-71791c7b1130.png">


```
In case there's some issue with the Process Payment entire data will be rolled back. Not a single 
data is inserted to db that's how transaction handled at monolithic.


Microservices generally follow database per service pattern. As we can see in the below images, 
2 different databases are used. For monolithic the approach should be the same as monolithic.
```

<img width="1312" alt="Screenshot 2023-04-16 at 1 02 21 PM" src="https://user-images.githubusercontent.com/43849911/232280625-800124a6-995f-4932-aed2-0e641ef20f31.png">

<img width="861" alt="Screenshot 2023-04-16 at 1 03 59 PM" src="https://user-images.githubusercontent.com/43849911/232280693-513fb6c4-1b1c-4fa2-947f-ef6eb35c7788.png">

<img width="906" alt="Screenshot 2023-04-16 at 1 07 31 PM" src="https://user-images.githubusercontent.com/43849911/232280834-d03f8a09-19a8-4114-ace7-ff99cea6efb8.png">

```
1. It's not a good approach to fire n number of HTTP requests. 
Eveytime a new service is added, HTTP request needs to be fired.
2. It will impact on the revenue is there's a application down time.

To overcome this issue, microservices provided a pattern called saga pattern.

We can implement saga pattern using two approaches:
1. Choreography
2. Orchestration

We can use Choreography pattern with the help of event sourcing so there will be no HTTP req call.

Following pic can be used to understand how transaction is done with the help of kafka topics 
and there are no HTTP event calls:
```

<img width="1066" alt="Screenshot 2023-04-16 at 1 13 03 PM" src="https://user-images.githubusercontent.com/43849911/232281073-b2c1bbf2-52c4-4379-bc50-5cbc15cf38ef.png">

<img width="1258" alt="Screenshot 2023-04-16 at 1 16 01 PM" src="https://user-images.githubusercontent.com/43849911/232281740-9c8fbd18-f32a-4b0a-864d-e7730ec821de.png">

<img width="1238" alt="Screenshot 2023-04-16 at 1 20 27 PM" src="https://user-images.githubusercontent.com/43849911/232283040-a9d9a697-5652-4096-b06d-bbd1e8038785.png">

<img width="1564" alt="Screenshot 2023-04-16 at 1 23 10 PM" src="https://user-images.githubusercontent.com/43849911/232283359-81ec4e3d-47c6-4c4d-900e-72f99cedc4e0.png">

```

```
