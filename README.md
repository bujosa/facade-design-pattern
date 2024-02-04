# Facade Design Pattern

The Facade design pattern provides a simplified interface to a complex subsystem. It involves a single wrapper class which contains a set of members required by the client. These members access the system on behalf of the facade client and hide the implementation details.

In the provided Go code, the facade pattern is used to simplify the process of retrieving weather data from the OpenWeatherMap API.

## Code Explanation

The code defines a `CurrentWeatherDataRetriever` interface with two methods: `GetByGeoCoordinates` and `GetByCityAndCountryCode`. These methods are used to retrieve weather data either by geographical coordinates or by city and country code.

The `CurrentWeatherData` struct implements this interface. It contains an `APIkey` field and uses it to make HTTP requests to the OpenWeatherMap API.

The `Weather` struct is a data structure that maps to the JSON response from the OpenWeatherMap API. It contains fields for various weather parameters like temperature, pressure, humidity, etc.

The `doRequest` method is a helper method that performs the actual HTTP request to the OpenWeatherMap API, checks the response status code, and parses the response body into a `Weather` struct.

The `responseParser` method is used to parse the HTTP response body into a `Weather` struct.

The `GetByGeoCoordinates` and `GetByCityAndCountryCode` methods use the `doRequest` method to retrieve weather data from the OpenWeatherMap API. They format the API URL with the appropriate parameters and pass it to the `doRequest` method.

In this way, the `CurrentWeatherData` struct acts as a facade, providing a simple interface for retrieving weather data and hiding the complexities of making HTTP requests and parsing JSON responses.

## Running the Tests

To run the tests, you will need to pass in your OpenWeatherMap API key and a flag to indicate whether to run integration tests. You can do this using the `-args` flag with the `go test` command.

Here is an example:

```bash
go test -args -apikey=your_api_key -integration=true
```

## Documentation

You can find the official documentation for the OpenWeatherMap API [here](https://openweathermap.org/api).