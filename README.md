# To-do application using Node.js

## Simple application developed for Rocketseat's Ignite Node.js Trail - Chapter I Challenge 2.

Challenge used as bsae the solution of the previous Challenge 1.

# During the development of this application for this challenge, I practiced the following topics of Node.js:

- Build routes;
- Create and use middleware;
- REST request parameters;
- Request testing with Insomnia;
- Troubleshooting based in Jest test results

# Middleware created:
- *checksExistsUserAccount*   
  receives the `username` via request header and checks if a user with the given username exists. In positive case, the `user` is passed to the `request` and the next function is called. Else, the error code `404` is given.  

- *checksCreateTodosUserAvailability*  
  receives the `user` in the `request` and checks if the `user` is a "free" user (`user.pro == false`) and if the number of todos equal or more than 10. In positive case, the error code `403` is given. Else, the next function is called.

- *checksTodoExists*  
  receives the `username` via request header and the a todo `id` via `request.params`. Then, this middleware function checks:  
  1) if a `user` with the given `username` exists;  
  2) if the given `id` is a uuid;  
  3) if a todo with the given `id` exists for the user;  
  If all checks are ok, the `todo` is passed to the `request` and the next function is called. Else, an error code is given (400 if `id`is not a uuid, 404 is `user`/`id` is not found).

- *findUserById*  
  receives a user `id` via `request.params` and checks if a user with the given `id` exists. In positive case, the user is passed to the `request` and the next function is called. Else, the error code 404 is given.