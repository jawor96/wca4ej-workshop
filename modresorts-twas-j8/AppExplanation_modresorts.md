# Executive summary of important application functionalities
Project is a Java web application that provides a range of functionality related to online reservation and management.

After analysis we have found following services: 
	1. class: com.acme.modres.SecondFilter method: doFilter
	2. class: com.acme.modres.FirstFilter method: doFilter
	3. class: com.acme.modres.LogoutServlet method: doGet
	4. class: com.acme.modres.AvailabilityCheckerServlet method: doGet
	5. class: com.acme.modres.WelcomeServlet method: doGet
	6. class: com.acme.modres.WeatherServlet method: doGet
	7. class: com.acme.modres.UpperServlet method: doGet.
We will summarize the functionality of each of them below.

## Summary of service with entry method: doFilter in class: com.acme.modres.SecondFilter
The purpose of the SecondFilter app is to process and modify the request sent to it before it is sent to the target resource and the response received from the target resource before it is sent back to the client.
The input provided to the SecondFilter app is a servlet request and a servlet response. The output returned by the SecondFilter app is a modified version of the servlet request and response.
The doFilter method utilizes the BufferedReader and PrintWriter classes to read the request content and write the response content. It also utilizes the FilterChain class to pass the request and response to the next filter in the filter chain.
## Summary of service with entry method: doFilter in class: com.acme.modres.FirstFilter
The purpose of the `FirstFilter` app is to filter requests and add a default user name to the request if no user name is provided. The filter adds a welcome message to the response and then passes the request on to the next filter in the chain.
The input to the `FirstFilter` app is a servlet request and response, as well as a filter chain. The output is a filtered response with a welcome message and the next filter in the chain is invoked.
The `doFilter` method utilizes the `HttpServletRequest` and `HttpServletResponse` objects to get the user name from the request and set the response content type and writer. If the user name is null, a default user name is set. The welcome message is then written to the response writer, and the filter chain is invoked to pass the request on to the next filter in the chain.
## Summary of service with entry method: doGet in class: com.acme.modres.LogoutServlet
### Business Purpose
The `LogoutServlet` app is used to log users out of their WSO2 Identity Server sessions by invalidating their SSO cookies. This ensures that any further requests made by the user to the server are rejected until they re-authenticate themselves.
### Input and Output
- **Input**: The `LogoutServlet` app takes in a `HttpServletRequest` and `HttpServletResponse` object as input. These objects are used to access the user's SSO cookies and to redirect them to the login page after logging out.
- **Output**: The `LogoutServlet` app returns a redirect response to the login page (`login.jsp`) upon successful logout.
### Methodology
1. `doGet` method: This method is used to handle HTTP GET requests to the `/logout` URL. It utilizes the `WSSecurityHelper` class to revoke the user's SSO cookies by calling the `revokeSSOCookies` method.
2. `revokeSSOCookies` method: This method is used to invalidate the user's SSO cookies by setting their expiration dates to the past. It takes in the `HttpServletRequest` and `HttpServletResponse` objects as input, and sends the user to the login page (`login.jsp`) after revoking the cookies.
## Summary of service with entry method: doGet in class: com.acme.modres.AvailabilityCheckerServlet
AvailabilityCheckerServlet is a Java servlet that provides availability information for a specific date. The purpose of this servlet is to check the availability of a reservation on a specific date and return the result to the client in JSON format.
Input: The servlet takes a request parameter "date" which contains the date for which the availability is to be checked.
Output: The servlet returns a JSON object with a "availability" field that contains a boolean value indicating whether there is an available reservation on the specified date.
Methodology:
The doGet method of the servlet is the main entry point for the servlet. It retrieves the selected date from the request parameter "date", and passes it to the ReservationCheckerData object for parsing. If the date is parsed successfully and there is a valid reservation list, a thread is created to run the DateChecker class. The thread is joined to wait for the DateChecker to finish its execution.
The DateChecker class uses the selected date to check for availability, and updates the ReservationCheckerData object with the result. The servlet then checks the availability status in ReservationCheckerData and sets the appropriate status code in the response. Finally, the servlet writes the availability status to the response in JSON format.
## Summary of service with entry method: doGet in class: com.acme.modres.WelcomeServlet
WelcomeServlet app is a simple Servlet application that generates a response with a plain text message "Enjoy!" for any GET request.
The purpose of this app is to demonstrate the use of Servlet API to generate a response in a Servlet.
The input to WelcomeServlet app is an HTTP GET request, and the output is a plain text response with the message "Enjoy!".
The doGet method of WelcomeServlet app is the main method that is invoked when an HTTP GET request is received. It sets the content type of the response to "text/plain", obtains a PrintWriter object to write to the response, and writes the message "Enjoy!"to the response. Finally, the PrintWriter object is closed.
## Summary of service with entry method: doGet in class: com.acme.modres.WeatherServlet
1. Business purpose:
The WeatherServlet app is a Java servlet that provides weather information to users. The app utilizes a third-party weather API to retrieve real-time weather information for a given city, and returns the information to the user in JSON format.
2. Input and Output:
Input:
The WeatherServlet app takes in a request from a user, which includes the name of the city for which weather information is requested.
Output:
The WeatherServlet app returns weather information for the requested city in JSON format.
3. Methodology:
The WeatherServlet app utilizes the doGet method to handle HTTP GET requests from users. When a GET request is received, the app retrieves the weather information for the requested city from a third-party weather API. The app then returns the weather information to the user in JSON format.
The getRealTimeWeatherData method is responsible for making the API call and retrieving the weather information for the requested city. The getDefaultWeatherData method provides a default weather information in the event that the API call fails or if the weather API key is not found.
The DefaultWeatherData class provides the default weather information for supported cities. The class loads the default weather information from a JSON file and returns it to the WeatherServlet app.
## Summary of service with entry method: doGet in class: com.acme.modres.UpperServlet
1. Business purpose: The purpose of the UpperServlet app is to capitalize the input string that is provided in the "input" parameter and return the capitalized string in the response.
2. Input and Output: The input to the UpperServlet app is a string that is provided in the "input" parameter. The output is a capitalized version of the input string.
3. Methodology: The doGet method of the UpperServlet app takes the input string from the "input" parameter, capitalizes it, and returns the capitalized string in the response. The ResponseUtils.encodeDataString method is used to escape any special characters in the input string.
