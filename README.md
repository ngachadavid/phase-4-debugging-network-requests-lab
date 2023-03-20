# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```console
$ bundle install
$ rails db:migrate db:seed
$ rails s
```

Then, in a new terminal, run the frontend:

```console
$ npm install --prefix client
$ npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged:
  I resolved an internal server error by first observing it on the console, then investigating the Rails logs to determine its root cause, and finally fixing the specific line of code that was identified in the logs

- Update the number of likes for a toy

  - How I debugged:
  I found a SyntaxError on the console because the JSON input ended unexpectedly. To locate the error source, I checked the Networks tab and saw that there was no Content even though the status was 204. The Rails server terminal displayed the same status, meaning that nothing was being rendered. To solve this, I added a render statement to the update method

- Donate a toy to Goodwill (and delete it from our database)

  - How I debugged:
  "I encountered a 'DELETE 404 not found' error message which indicated that the route was not defined. To address this issue, I added ':destroy' to the routes in the 'config/routes.rb' file
