# PS-get-deep-property exercise

## Instructions

- Using vanilla javascript, create a function that gets the value of a property at a given path
- Example:
  - If given the object: {person: {name: {first: 'FirstName', middleInitial: 'I', lastName: 'LastName''}}}
  - And given the path: 'person.name.lastName'
  - The output would be: 'LastName'
- After you complete the exercise, provide any notes on your code below such as how to run your example

## Sample Code Structure
```javascript
function getDeepProperty(obj, path) {
        // See if there is more to the path 
        if (path.indexOf('.') >= 0) {

            var pathParts = path.split(".");

            // If this segment of the path is undefined, let the user know.  
            // Otherwise, send this portion of the object branch and path back to this very function.
            return obj[pathParts[0].toString()] === undefined ? "undefined at " + pathParts[0].toString(): 
            getDeepProperty(obj[pathParts[0].toString()], path.substring(path.indexOf(".") + 1));

        } else {
            // We are at the end of the path. Return the value if it exists, where the path failed if not.
            return obj[path] === undefined ? "undefined at " + path: obj[path];
        }
    }

    const someObj = {person: {name: {firstName: 'FirstName', middleInitial: 'I', lastName: 'LastName'}}};
    const value = getDeepProperty(someObj, 'person.name.firstName');
```

## Candidate Notes:
- I created a file that will run this example - getDeepProperty.html.
- Load the file into a browser.
- Input the portion of the path for which you want a value and hit the "Find Value" button.
- The onclick event of the button calls the function.
- In the real world, I would add more error checking such as a period at the end of the string
- input by the user but I felt like the above would do for now.