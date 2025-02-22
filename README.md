# Express.js Route Handler: Missing Error Handling for Invalid User IDs

This repository demonstrates a common error in Express.js route handlers:  lack of error handling for invalid input, specifically non-numeric user IDs in this case.

## Bug

The `bug.js` file contains a route handler that retrieves a user by ID.  It uses `parseInt` to convert the ID from a string to an integer but lacks crucial error handling.  If a non-numeric ID is passed, `parseInt` will return `NaN`, causing the `find` method to fail silently or throw an error depending on the environment.  This can lead to unpredictable behavior such as unexpected 404 errors or server crashes.

## Solution

The `bugSolution.js` file demonstrates the correct approach.  It includes explicit checks to ensure the `userId` is a valid number before attempting to access the user data.  If the ID is invalid, it returns an appropriate error response, providing a better user experience and preventing potential server errors.

## How to reproduce the bug

1.  Clone this repository.
2.  Run `node bug.js`.
3.  Send a GET request to `/users/abc` (or any non-numeric ID).

## How to run the solution

1.  Clone this repository.
2.  Run `node bugSolution.js`.
3.  Send a GET request to `/users/abc` (or any non-numeric ID).  Observe the appropriate error response.
