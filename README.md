+ OpenWeather API - QA Testing Suite

A comprehensive automated testing suite for OpenWeather API endpoints with focus on Tunisian geographic locations. This project validates weather data accuracy, API response integrity, and error handling mechanisms using Postman collections and Newman automation.

+ Project Overview

This testing suite covers critical OpenWeather API functionality including current weather data retrieval, GPS coordinate-based queries, weather forecasting, and comprehensive error scenario validation. The implementation includes 29 automated test assertions across 6 distinct API endpoints with specialized validations for Tunisia climate patterns.

+ Test Coverage

- Current Weather Data: City-based queries for Tunis and Radès
- Coordinate-based Weather: GPS precision testing using Tunis coordinates
- Weather Forecasting: 5-day forecast validation with data structure verification
- Error Handling: Invalid API key authentication and non-existent city scenarios
- Performance Testing: Response time validation and data transfer optimization

+ Key Features

- Zero-failure test execution with 100% assertion pass rate
- Climate-specific validations adapted to Tunisian weather patterns
- Comprehensive JSON structure validation
- HTTP status code verification (200, 401, 404)
- Dynamic environment variable configuration
- Professional HTML report generation

+ Prerequisites

+ System Requirements

- Node.js (version 12.0.0 or higher)
- npm (Node Package Manager)
- Valid OpenWeather API key

+ Dependencies Installation

```bash
# Install Newman globally
npm install -g newman

# Install Newman HTML reporter
npm install -g newman-reporter-html
```

+ API Key Setup

1. Create account at [OpenWeather](https://openweathermap.org/api)
2. Generate free API key
3. Configure environment variables as specified in setup section

+ Installation

+ Clone or Download Project Files

```bash
# Download the collection file
# OpenWeather_API_QA_Tests_Tunisia.postman_collection.json
```

+ Environment Configuration

Create Postman environment with following variables:

```json
{
  "base_url": "https://api.openweathermap.org/data/2.5",
  "api_key": "YOUR_API_KEY_HERE"
}
```

+ Execution

+ Command Line Execution

```bash
# Basic test execution
newman run OpenWeather_API_QA_Tests_Tunisia.postman_collection.json \
  --environment OpenWeather_Tunisia.postman_environment.json

# Execute with HTML report generation
newman run OpenWeather_API_QA_Tests_Tunisia.postman_collection.json \
  --environment OpenWeather_Tunisia.postman_environment.json \
  --reporters html \
  --reporter-html-export report.html

# Execute with detailed console output
newman run OpenWeather_API_QA_Tests_Tunisia.postman_collection.json \
  --environment OpenWeather_Tunisia.postman_environment.json \
  --reporters cli,html \
  --reporter-html-export detailed_report.html \
  --verbose
```

+ Environment Variable Override

```bash
# Override API key via command line
newman run OpenWeather_API_QA_Tests_Tunisia.postman_collection.json \
  --env-var "api_key=YOUR_API_KEY" \
  --env-var "base_url=https://api.openweathermap.org/data/2.5"
```

+ Report Generation

+ HTML Report Access

After execution with HTML reporter:

1. Locate generated `report.html` file in execution directory
2. Open file in web browser
3. Review detailed test results, response times, and assertion outcomes

+ Report Contents

- Execution Summary: Total tests, pass/fail rates, duration metrics
- Request Details: Individual endpoint results with response data
- Performance Metrics: Response times, data transfer statistics
- Assertion Results: Detailed validation outcomes for each test
- Error Analysis: Comprehensive error scenario validation results

+ Continuous Integration Integration

```bash
# CI/CD pipeline execution
newman run collection.json \
  --environment environment.json \
  --reporters junit,html \
  --reporter-junit-export results.xml \
  --reporter-html-export report.html \
  --bail
```

+ Test Structure

+ Endpoint Coverage

| Endpoint | Method | Purpose | Assertions |
|----------|--------|---------|------------|
| `/weather` | GET | Current weather by city | 8 tests |
| `/weather` | GET | Current weather by coordinates | 4 tests |
| `/weather` | GET | Current weather Radès | 6 tests |
| `/forecast` | GET | 5-day weather forecast | 5 tests |
| `/weather` | GET | Invalid API key error | 3 tests |
| `/weather` | GET | City not found error | 3 tests |

+ Validation Categories

- HTTP Response Validation**: Status codes, headers, response times
- Data Structure Validation**: JSON schema compliance, required fields
- Business Logic Validation**: Temperature ranges, geographic accuracy
- Error Response Validation**: Error codes, error messages, error structure

+ Performance Benchmarks

- Average Response Time**: 252ms
- Maximum Acceptable Response Time**: 2000ms
- Total Execution Duration**: 2.1 seconds
- Data Transfer Efficiency**: 16.89KB total payload

+ Troubleshooting

+ Common Issues

+API Key Authentication:

```bash
# Verify API key validity
curl "https://api.openweathermap.org/data/2.5/weather?q=Tunis&appid=YOUR_API_KEY"
```

+Network Connectivity:

```bash
# Test API endpoint accessibility
curl -I "https://api.openweathermap.org/data/2.5/weather"
```

+Newman Installation:

```bash
# Verify Newman installation
newman --version

# Reinstall if necessary
npm uninstall -g newman
npm install -g newman
```

+ Error Resolution

- **401 Unauthorized**: Verify API key configuration in environment variables
- **404 Not Found**: Confirm city names and coordinate accuracy
- **Network Errors**: Check internet connectivity and API endpoint availability
- **Report Generation Failures**: Ensure write permissions in execution directory

+ Contributing

+ Test Enhancement Guidelines

- Maintain existing assertion structure
- Add comprehensive error handling for new endpoints
- Include performance benchmarks for new test scenarios
- Update documentation for additional geographic regions

+ Code Standards

- Use descriptive test names following existing patterns
- Implement proper assertion chaining for complex validations
- Include response time validation for all new endpoints
- Maintain environment variable abstraction for configuration

+ License

This testing suite is provided for educational and professional development purposes. OpenWeather API usage subject to OpenWeather terms of service and API key limitations.