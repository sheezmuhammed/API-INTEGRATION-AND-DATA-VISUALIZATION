# API-INTEGRATION-AND-DATA-VISUALIZATION

**COMPANY**:CODTECH IT SOLUTIONS
**NAME**:SHEEZ MUHAMMED C
**INTERN ID**:CT08NAH
**DOMAIN**:PYTHON
**BATCH DURATION**:January 15th/2025 to February 15th/2025
**DESCRIPTION**:

This Python script fetches weather forecast data for a specified city using the OpenWeatherMap API and visualizes temperature trends using Matplotlib and Seaborn. The script extracts temperature values from the forecasted data and plots a time-series graph, making it easier to observe temperature variations over the next few days.

Key Features
	•	Uses the requests library to fetch real-time weather forecast data from OpenWeatherMap.
	•	Extracts date, time, and temperature values from the API response.
	•	Uses Seaborn and Matplotlib to create a visually appealing line plot of temperature trends.
	•	The x-axis represents date and time, while the y-axis shows temperature values in degrees Celsius.
	•	The graph includes markers on data points, a grid, and rotated x-axis labels for better readability.

Code Breakdown

1. Installing Required Libraries

Before running the script, install the necessary libraries using:

pip install requests matplotlib seaborn

	•	requests – To make API calls and retrieve weather data.
	•	matplotlib.pyplot – To create and customize plots.
	•	seaborn – To enhance the visual appearance of the plot.

2. Fetching Weather Data

The script requests a 5-day forecast (every 3 hours) from the OpenWeatherMap API. You need to replace "your_api_key_here" with your API key from OpenWeatherMap.

API_KEY = "your_api_key_here"
CITY = "New York"
url = f"http://api.openweathermap.org/data/2.5/forecast?q={CITY}&appid={API_KEY}&units=metric"
response = requests.get(url)
data = response.json()

	•	API_KEY: Replace with your personal API key.
	•	CITY: The name of the city for which the forecast is required.
	•	The API returns a JSON response containing detailed weather data.

3. Extracting Relevant Data

From the API response, the script extracts:
	•	dates: List of timestamps when the forecast is recorded.
	•	temperatures: List of corresponding temperature values in Celsius.

dates = [item['dt_txt'] for item in data['list']]
temperatures = [item['main']['temp'] for item in data['list']]

4. Plotting the Temperature Trend

The extracted data is used to generate a temperature trend line plot:

plt.figure(figsize=(12, 6))
sns.lineplot(x=dates, y=temperatures, marker='o')
plt.xticks(rotation=45)
plt.title(f'Temperature Trend in {CITY}')
plt.xlabel('Date & Time')
plt.ylabel('Temperature (°C)')
plt.grid(True)
plt.tight_layout()
plt.show()

	•	plt.figure(figsize=(12,6)): Sets the plot size.
	•	sns.lineplot(x=dates, y=temperatures, marker='o'): Creates a line plot with circular markers on each data point.
	•	plt.xticks(rotation=45): Rotates x-axis labels for better visibility.
	•	plt.grid(True): Adds a grid for easier data interpretation.
	•	plt.tight_layout(): Adjusts layout to prevent overlapping.

How to Use This Script
	1.	Get an API Key
	•	Sign up at OpenWeatherMap to obtain a free API key.
	2.	Install Dependencies
	•	Run pip install requests matplotlib seaborn.
	3.	Modify the Script
	•	Replace "your_api_key_here" with your OpenWeatherMap API key.
	•	Change the CITY variable to fetch data for a different location.
	4.	Run the Script
	•	Execute the Python script and view the temperature trend graph.

Conclusion

This script provides an easy way to visualize upcoming temperature trends for a chosen city.
By modifying the API key and city name, users can fetch and analyze weather data for any location worldwide.
