# Fuel Efficiency Data Analytics Platform

This document outlines the progress and changes made to the Fuel Efficiency Data Analytics Platform.

## Introduction

The Fuel Efficiency Data Analytics Platform is a web application designed to automatically gather, process, and present the most recent fuel efficiency statistics for various fuel types, providing users with insightful analytics in a user-friendly UI.

## Changes and Progress

### Updated Flask Application

- Set up a basic Flask server in `app.py`.
- Integrated Kaggle API to download datasets directly from Kaggle.
- Handled authentication for the Kaggle API using the `kaggle.json` file.

### Data Processing

- Implemented a function to retrieve the fuel economy dataset from Kaggle.
- Used Pandas to read the CSV data into a DataFrame.

### Frontend Development

- Created a basic HTML template to display the data.
- Utilized Bootstrap to style the frontend for a responsive design.
- Added custom CSS to enhance the visual appearance of the data presentation.

### Error Handling and Email Notifications

- Implemented a custom error handler for HTTP 500 Internal Server Errors.
- When an unhandled exception occurs in the application, such as a programming error or an unexpected issue, this error handler is triggered.
- An email notification is sent to the developer, including error details.

### CSV Data Download

- Added a functionality to allow users to download the fuel data in CSV format.
- Users can access this feature through the `/download-data` endpoint.

### Filtering and Search

- Added filtering options to allow users to search and filter the data based on their preferences.
- Users can filter by make, model, and fuel type.

### Data Visualization

#### Page 1: Average Annual Fuel Cost by Fuel Type 1

- Created a bar chart displaying the average annual fuel cost by Fuel Type 1.
- Users can visualize and compare fuel costs for different fuel types.

#### Page 2: Average Annual Fuel Cost by Fuel Type 2

- Generated a bar chart displaying the average annual fuel cost by Fuel Type 2.
- This chart provides insights into the costs associated with different fuel types.

#### Page 3: Top 5 Makes with Lowest Average Annual Fuel Cost (FT1)

- Developed a bar chart showcasing the top 5 car makes with the lowest average annual fuel cost (Fuel Type 1).
- Users can identify cost-effective car makes.

#### Page 4: Top 5 Makes with Lowest Average Annual Fuel Cost (FT2)

- Created a Plotly bar chart presenting the top 5 car makes with the lowest average annual fuel cost (Fuel Type 2).
- The chart offers interactive features for a richer data exploration experience.

  ### Page 5: Average Annual Fuel Cost by Year for FT1 and FT2

- Developed a dynamic line chart on Page 5 (`/page5`) using Google Charts to display the average annual fuel cost over the years for Fuel Type 1 (FT1) and Fuel Type 2 (FT2).
- The chart illustrates the historical trends of annual fuel costs, allowing users to hover over the lines to see exact values for any given year, all in USD.
- This visualization provides insights into the changing costs of fuel over time and highlights the potential impact of technological advancements on fuel efficiency.
- Users can navigate back to the main page using the "Back to Main Page" button.

### Troubleshooting and Debugging

- Ensured that the Kaggle package was correctly installed and imported.
- Verified the presence and permissions of the `kaggle.json` file.
- Addressed issues with Flask not displaying data by confirming the data was correctly passed to the template.
- Debugged CSS linking issues to ensure that custom styles were applied.


## Running the Application

To run the Fuel Efficiency Data Analytics Platform:

1. Ensure that you have the required dependencies installed.
2. Organize HTML files into the 'templates' folder.
3. Run the Flask application by executing `app.py`.

The application can be accessed through a web browser.

## Usage

- Use the search and filter options on the main page (`/`) to explore the data.
- Download the fuel data in CSV format through the `/download-data` endpoint.
- Navigate to the different pages (Page 1, Page 2, Page 3, Page 4, Page 5) to visualize various aspects of fuel efficiency data.

### Error Handling and Email Notifications:

-Custom Error Handling: A custom error handler has been implemented for HTTP 500 Internal Server Errors in the Flask application. This error handler is designated using the @app.errorhandler(500) decorator.

-Email Notifications: In the event of a 500 Internal Server Error, an email notification mechanism has been integrated. The purpose is to promptly notify designated recipients, ensuring that developers are informed when such an error occurs.

-Message Composition: The error handling function constructs an email message using Flask-Mail. The message includes a subject, sender, recipients, and a body. The subject is set as "Internal Server Error," the sender's email address is specified, and the recipients' email addresses are configured to receive error notifications.

-Error Details Inclusion: The error handler extracts pertinent error details from the error parameter and includes them in the email message body. This ensures that developers receive comprehensive information about the error, aiding in the debugging and resolution process.

-Email Dispatch: The email message is dispatched using the mail.send(msg) method, leveraging the Flask-Mail extension's capabilities.
User-Friendly Error Page: To enhance the user experience, a custom 500 error page is rendered using render_template. This page can provide a user-friendly error message to site visitors, improving overall usability.


### CSRF (Cross-Site Request Forgery) Protection:
-CSRF Prevention: To bolster application security, CSRF protection has been implemented, guarding against Cross-Site Request Forgery attacks. This security measure is achieved through Flask-WTF, a Flask extension designed for CSRF protection.

-FlaskForm Integration: FlaskForm from flask_wtf has been imported to create forms with built-in CSRF protection.

-Secret Key Establishment: A secret key has been defined for the application using app.config['SECRET_KEY']. This secret key is pivotal for safeguarding session data, cookies, and CSRF tokens, fortifying the application's security.

-CSRFProtect Initialization: CSRF protection is activated by initializing a CSRFProtect object, named csrf, and associating it with the Flask application using csrf.init_app(app).


