## Challenge

mplement a node app called `fetcher.js`.

It should take two command line arguments:

1. a URL
2. a local file path

It should download the resource at the URL to the local path on your machine. Upon completion, it should print out a message like `Downloaded and saved 1235 bytes to ./index.html`.

## Solution

```javascript
// Require the 'request' and 'fs' modules
const request = require("request");
const fs = require("fs");
const readline = require("readline");

// Get URL and file path arguments from the command line
const url = process.argv[2];
const filePath = process.argv[3];

// If either argument is missing, print an error message and exit the script
if (!url || !filePath) {
  console.error("Usage: node fetcher.js <url> <file-path>");
  process.exit(1);
}

// check if file path already exists
fs.access(filePath, fs.constants.F_OK, (err) => {
  if (!err) {
    const rl = readline.createInterface({
      input: process.stdin,
      output: process.stdout,
    });

    rl.question(
      `${filePath} already exists. Do you want to overwrite (Y/N)?`,
      (answer) => {
        rl.close();
        if (answer.toUpperCase() !== "Y") {
          console.log("Aborting...");
          process.exit(0);
        } else {
          // send GET request to URL
          downloadResources();
        }
      }
    );
  } else {
    // if file doesnt exist, send GET request
    downloadResources();
  }
});

const downloadResources = function () {
  // Send GET request to URL using 'request'
  request(url, (error, response, body) => {
    // print an error message and exit if there was an error
    if (error) {
      console.error(`Error: ${error.message}`);
      return;
    }

    // print an error message and exit if status code is not 200
    if (response.statusCode !== 200) {
      console.error(`Request failed.\nStatus Code: ${response.statusCode}`);
      return;
    }

    // write the response body to the specified file path with 'fs' if the response is valid.
    fs.writeFile(filePath, body, (err) => {
      // print an error message and exit if there is an error writing file
      if (err) {
        console.error(`Error writing file: ${err.message}`);
        return;
      }

      // get file size
      fs.stat(filePath, (err, stats) => {
        if (err) {
          console.log(`Erro getting file stats: ${err.message}`);
          return;
        }

        const fileSize = stats.size;
        // print success message
        console.log(`Downloaded and saved ${fileSize} bytes to ${filePath}.`);
      });
    });
  });
};
```

## Explanation

- `reuquire` is used to load necessary modules like `reques`, `fs`, and `readline`
- Using `process.argv` we reaad the command line arguments to retrieve the URL and local file path.
- We check if both arguments were provided, if either of them are missing we print an error and exits.
- We then check if the file path already exists using `fs.access()`, if it does exist `readline` is used to prompt the user to confirm whether to overwrite the file or not. If the user doesnt want to overwrite the file, we abort. Otherwise we continue and call the `downloadResources` function.
- `downloadResources` function sends a GET request to the specified URL using `resuest`, we check for errors and invalid status codes, and print error messages and exit if necessary.
- If the repsonse is valide, we then write the repsonse body to the speicifed file path using `fs.writeFile()`, if there is an error writing the file, it prints an error message and exits.
- If the file is successfully written, we use `fs.stat()` to get the file size and print a message with the file size and path.
