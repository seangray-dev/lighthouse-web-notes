This code defines a set of function for making API requests to obtain the IP address, latitude and longitude coordinates of the user's current location, and the next time the ISS will fly over that location. The `request-promise-native` library is used to make the HTTP requests, which return promises to the that are resolved asynchronously.

This line imports the `request-promise-native` library and assigns it to a cariable called request:

```javascript
const request = require('request-promise-native');
```

This function uses the `request` library to fetch the user's IP address from the `https://api.ipify.org` API in JSON format. It returns the promise that is returned by the `request` function.

```javascript
const fetchMyIP = function () {
  return request('https://api.ipify.org?format=json');
};
```

This function takes the IP address obtained from the previous API call and fetches the latitude and longitude coordinates for that IP address from the `http://ipwho.is` API. It returns the promise that is returned by the `request` function.

```javascript
const fetchCoordsByIP = function (body) {
  const ip = JSON.parse(body).ip;
  return request(`http://ipwho.is/${ip}`);
};
```

This function takes the latitude and longitude coordinates obtained from the previous API call and fetches the next time the ISS will fly over that location from the https://iss-flyover.herokuapp.com API. It returns the promise that is returned by the request function.

```javascript
const fetchISSFlyOverTimes = function (body) {
  const { latitude, longitude } = JSON.parse(body);
  const url = `https://iss-flyover.herokuapp.com/json/?lat=${latitude}&lon=${longitude}`;
  return request(url);
};
```

This function chains the previous three functions together to obtain the user's current location and the next time the ISS will fly over it. It first calls `fetchMyIP` to obtain the user's IP address, then uses the result of that call as input to `fetchCoordsByIP` to obtain the latitude and longitude coordinates, and finally uses the result of that call as input to `fetchISSFlyOverTimes` to obtain the flyover times. The `then` method is used to chain the promises together so that each subsequent call waits for the previous one to finish before executing. The final `then` method extracts the `response` property from the API response and returns it, which contains the next ISS flyover time for the user's location.

```javascript
const nextISSTimesForMyLocation = function () {
  return fetchMyIP()
    .then(fetchCoordsByIP)
    .then(fetchISSFlyOverTimes)
    .then((data) => {
      const { response } = JSON.parse(data);
      return response;
    });
};
```
