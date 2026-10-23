# CS 465: Travlr Getaways

Travlr Getaways is a full stack web application with a customer website and an Angular administrative interface. The application uses MongoDB, Express, Angular, and Node.js, with authentication to protect changes to trip data.

## Architecture

The customer side uses Express to serve HTML pages built with Handlebars templates. HTML provides the page structure, while JavaScript handles server logic and retrieves trip information. Handlebars inserts that information into the page before it is sent to the browser. The administrative side uses an Angular single-page application, which updates views and retrieves data without requiring a full page reload for each interaction. Both sides use the same backend API, but they present the information differently. The customer website focuses on displaying trips, while the Angular application provides an interactive interface for managing them.

MongoDB was used because trip and user information fits naturally into documents. Its document structure works well with the objects used throughout the JavaScript application and allows the data model to change as requirements develop. Mongoose provides schemas and validation so that the application can maintain consistent records while using a flexible NoSQL database.

## Functionality

JavaScript is a programming language used to implement application behavior. JSON is a text format used to represent and exchange data. Unlike JavaScript, JSON does not contain executable functions or application logic. In this project, the API receives and returns JSON, allowing the frontend and backend to communicate using a shared data format. The backend retrieves records from MongoDB through Mongoose and returns them as JSON. The customer website uses that information to render its templates, while Angular uses it to populate components and forms.

One example of refactoring was replacing repeated trip content in static HTML with a Handlebars loop that generates the content from data. Shared headers and footers were also moved into partials. Another example was changing the customer controller from reading a local JSON file to retrieving trip information through the API. In Angular, the trip display was separated into a reusable trip-card component, and API requests were organized in a shared data service. These changes reduced repeated code and made updates easier to manage. Reusable UI components also keep the interface consistent because a change to one component applies everywhere that component is used.

## Testing

An endpoint identifies a resource or operation available through the API, while the HTTP method determines what the request does. For example, `GET /api/trips` retrieves the trip list, and `POST /api/trips` creates a trip. The `/api/trips/:tripCode` endpoint supports retrieving, updating, or deleting a specific trip through GET, PUT, and DELETE requests. Testing these operations involves checking response codes, returned data, and whether database changes match the request. It also requires checking error cases, such as requests for trips that do not exist.

Adding authentication introduces more conditions to test. The login endpoint checks credentials and returns a JSON Web Token after successful authentication. Requests that create, update, or delete trips require that token in the Authorization header. Testing must cover valid requests as well as requests with missing, invalid, or expired tokens. Public trip retrieval should still work without authentication. Hiding editing controls in the interface helps guide users, but the backend must enforce authentication because requests can be sent directly to the API.

## Reflection

I came into this course with experience building MERN applications, so this project gave me an opportunity to apply that experience while working with Angular instead of React. I strengthened my understanding of component organization, shared services, API integration, and authentication across the frontend and backend. Troubleshooting issues with image paths, data retrieval, and authorization headers also gave me more practice tracing problems between different parts of an application. This experience supports my goal of working in software development by showing that I can work with different frontend frameworks, connect them to a database through an API, and document how the application works.
