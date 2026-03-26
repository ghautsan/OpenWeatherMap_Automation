# OpenWeatherMap Automation Project

## Description
This project was built using **Katalon Studio** to perform API automation testing on the **OpenWeatherMap** service.  
Main objectives:
- Retrieve the **5-day weather forecast** for South Jakarta.
- Retrieve the **current air pollution** for South Jakarta.
- Validate the **response body**, **JSON schema**, and other important attributes (status code, headers, response time, required fields).
- Log the full response body for debugging and verification.

---

## How to Run the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/OpenWeatherMap_Automation.git

2. Open the project in Katalon Studio.

3. Run the Test Suite:
- Open Test Suites → WeatherSuite.
- Click Run to execute all test cases.

How to Get the Report
- After running WeatherSuite, Katalon automatically generates reports in the folder:

Reports/

- Reports can be exported to HTML or PDF via the Test Suite Report menu.

Test Cases
1. TC_Forecast_JakartaSelatan
 Endpoint:
https://api.openweathermap.org/data/2.5/forecast?lat=-6.25&lon=106.8&appid=${_API_KEY}

 Validations:
- Status code = 200
- Response body contains South Jakarta coordinates
- Forecast list is not empty
- Temperature is a Number type
- JSON structure matches schema (city, list, main)
- Other attributes: Content-Type header = application/json, response time < 2000 ms, required fields not null

 Logging:
KeywordUtil.logInfo(response.getResponseBodyContent())

2. TC_AirPollution_JakartaSelatan- Endpoint:
https://api.openweathermap.org/data/2.5/air_pollution?lat=-6.25&lon=106.8&appid=${_API_KEY}

 Validations:
- Status code = 200
- Response body contains South Jakarta coordinates
- AQI is an Integer type
- JSON structure matches schema (coord, list, main, components)
- Other attributes: Content-Type header = application/json, response time < 2000 ms, required fields not null

 Logging:
KeywordUtil.logInfo(response.getResponseBodyContent())

Project Structure
OpenWeatherMap_Automation/
├── Object Repository/       # API request objects
│   ├── Forecast_JakartaSelatan
│   └── AirPollution_JakartaSelatan
├── Test Cases/              # Test case scripts
│   ├── TC_Forecast_JakartaSelatan
│   └── TC_AirPollution_JakartaSelatan
├── Test Suites/             # Test suite bundling test cases
│   └── WeatherSuite
├── Reports/                 # Test execution reports
└── README.md                # Project documentation

Notes
- Use coordinates (lat/lon) for South Jakarta to avoid "city not found" errors.
- Ensure your API key is active and does not exceed the free tier rate limit.
- The KeywordUtil.logInfo(response.getResponseBodyContent()) line ensures the full JSON response body is visible in the Log Viewer for debugging.
