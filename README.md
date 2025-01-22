### sheets-geocoding
Google Sheets Volunteer Location Geocoding - Dream Studio Project

## README: Google Sheets Geocoding Script

### Overview
This Google Apps Script enables geocoding for locations in a Google Sheet. It automatically fetches latitude, longitude, and PlusCode values for specified locations using the Google Geocoding API. Additionally, the script includes functionality to populate missing values and dynamically update when the location column is modified.

### Features
1. Automated Geocoding:

Fetches latitude and longitude using the Google Geocoding API.
Converts latitude and longitude into PlusCode using an embedded encoding function.

2. Real-Time Updates:

Listens for changes in the "Location" column and dynamically updates latitude, longitude, and PlusCode values.

3. Manual Trigger:

A function (populateMissingCoordinates) to fill in missing geocoding information across the entire sheet.

4. Custom PlusCode Generation:

Encodes latitude and longitude into a PlusCode using the encode function.

### Setup Instructions

1. Prerequisites

- Google Cloud Platform (GCP):

Set up a Google Cloud project and enable the Geocoding API.
Generate an API key for accessing the Geocoding API.

- Google Sheets:

Have a Google Sheet with the following columns:
Column E (Location): Address or location input.
Column G (Latitude): Latitude of the location.
Column H (Longitude): Longitude of the location.
Column I (PlusCode): Encoded PlusCode for the location.

2. Adding the Script

Open your Google Sheet.
Navigate to Extensions > Apps Script.
Copy and paste the provided script into the Apps Script editor.
Replace the API_KEY placeholder with your Google Geocoding API key.
Save the project (File > Save).

3. Authorization
The first time you run the script, you will be prompted to authorize it. Follow the prompts to grant necessary permissions.

### Functions

1. geocodeLocation()
Iterates through the sheet and populates latitude, longitude, and PlusCode values for locations in the "Location" column that are missing data.
2. fetchGeocodeData(location)
Sends a request to the Google Geocoding API and retrieves latitude and longitude for the given location.
3. encode(lat, lng, codeLength = 10)
Encodes latitude and longitude into a PlusCode using a base-20 encoding algorithm.
4. onEdit(e)
Triggered automatically when a cell in the "Location" column is modified. Updates latitude, longitude, and PlusCode in real time.
5. populateMissingCoordinates()
Manually triggers geocoding for all rows with missing latitude, longitude, or PlusCode data.

### How to Use

- Automated Updates
Add a location (address) to a cell in the "Location" column (Column E).
Latitude, longitude, and PlusCode will be populated automatically.

- Manual Trigger
Open the Apps Script Editor.
Run the populateMissingCoordinates function to process all rows with missing data.

#### Notes
Quota Limits:
The Geocoding API has usage limits. Monitor your API usage in GCP to avoid exceeding the free tier.
Error Handling:
If the Geocoding API fails, a log message is created in the Apps Script Logger.
Real-Time Trigger:
The onEdit function ensures that geocoding updates are made dynamically when the "Location" column is edited.

#### Troubleshooting
Geocoding API Errors:
Check the validity of the API key and ensure the Geocoding API is enabled in your GCP project.
No Data Returned:
Ensure the location input is accurate and properly formatted (e.g., "City, State" or "Address, Zip Code").
PlusCode Errors:
Verify latitude and longitude values are correctly populated before encoding to PlusCode.

#### Future Enhancements
Add functionality to handle batch geocoding with exponential backoff for API limits.
Include support for reverse geocoding (coordinates to address).
Enhance error reporting with email notifications.

#### API Key Security
Important: Do not expose your API key publicly. Consider using a secure storage solution or obfuscating the key in production environments.

#### Acknowledgments
Google Geocoding API for providing geolocation data.
Open Location Code for the PlusCode encoding algorithm.
ChatGPT was used to refine the code and README. 
