Questions (10/9/2019)

1. Should the order of line no. 9  and 10 matter in the dockerfile ? If it does why ? And what would be a more correct order  ?

2. Optimize the Dockerfile so that the final image is as small as possible.

3.a Create directory within containers-session/<your-name>/multicontainer-app
3.b In containers-session/<your-name>/multicontainer-app Create three directories namely frontend, backend, db.
3.c In the frontend directory add code, Dockerfile to create an image and launch container of the frontend in language of your choice.
3.d In the backend directory add code, Dockerfile to create an image and launch container of the backend in language of your choice. 
3.e In the db directory add code, Dockerfile to create an image and launch container of the db in language of your choice.
3.f Frontend should be able to call backend API to add values to a table in the DB. Could be as simple as adding name and phonenumber to a table in the db.
3.g Write shell script to run the containers in such an order that nothing fails. 

Rules: 
1>  No docker, only podman to be used.
2>  db should be persistent and needs to have a volume attached.
3>  No docker-compose / any orchestration.
4>  You can program in any langauge. 
5>  Ask questions to anyone at anytime, do not hesitate to ask any doubt. Do research before asking.