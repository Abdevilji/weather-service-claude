# Weather Service with Claude and Cursor

This project provides a weather service that can be accessed through Claude and Cursor's inbuilt chat. It uses the National Weather Service (NWS) API to provide real-time weather alerts and forecasts.

## Features

- Get weather alerts for any US state
- Get detailed weather forecasts for specific locations
- Real-time weather updates
- Easy integration with Claude and Cursor

## Setup

1. Make sure you have Python 3.11+ installed
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Running the Server

To start the weather service:

```bash
python server/weather.py
```

The server will start on `http://0.0.0.0:8000` using SSE (Server-Sent Events) transport.(Default)

## Using with Claude

You can interact with the weather service through Claude in two ways:

1. **Using MCP in Cursor:**
   - Open the MCP panel in Cursor
   - Use the following commands:
     ```python
     # Get weather alerts for California
     get_alerts("CA")
     
     # Get weather forecast for Los Angeles
     get_forecast(34.0522, -118.2437)
     ```

2. **Using Cursor's Inbuilt Chat:**
   - Open the chat interface in Cursor
   - Ask questions like:
     - "What's the weather in California?"
     - "Are there any weather alerts in CA?"
     - "What's the forecast for Los Angeles?"

## Available Commands

### Weather Alerts
```python
get_alerts(state: str) -> str
```
- `state`: Two-letter US state code (e.g., "CA" for California)
- Returns: Formatted string with active weather alerts

### Weather Forecast
```python
get_forecast(latitude: float, longitude: float) -> str
```
- `latitude`: Location's latitude
- `longitude`: Location's longitude
- Returns: Formatted string with weather forecast

## Example Usage

1. **Getting Weather Alerts:**
   ```python
   # Get alerts for California
   alerts = get_alerts("CA")
   print(alerts)
   ```

2. **Getting Weather Forecast:**
   ```python
   # Get forecast for Los Angeles
   forecast = get_forecast(34.0522, -118.2437)
   print(forecast)
   ```

## Error Handling

The service includes proper error handling for:
- Network issues
- Invalid API responses
- Invalid input parameters

## Stopping the Server

To stop the server, press `CTRL+C` in the terminal where it's running.

## Notes

- The service uses the National Weather Service API
- All times are in Pacific Daylight Time (PDT)
- Weather alerts are updated in real-time
- Forecasts are typically updated every few hours

## Troubleshooting

If you encounter issues:
1. Make sure the server is running
2. Check your internet connection
3. Verify the state code or coordinates are correct
4. Ensure you have the latest version of the dependencies

## License

This project is open source and available under the MIT License.
