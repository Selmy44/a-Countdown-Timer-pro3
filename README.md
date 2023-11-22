# a-Countdown-Timer-pro3
This is a web a Countdown Timer platform
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Weather App</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
    }
    .weather-container {
      margin-top: 50px;
    }
  </style>
</head>
<body>
  <h1>Weather App</h1>
  <input type="text" id="cityInput" placeholder="Enter city">
  <button onclick="getWeather()">Get Weather</button>
  <div class="weather-container">
    <h2 id="city"></h2>
    <p id="temperature"></p>
    <p id="description"></p>
  </div>

  <script>
    function getWeather() {
      const city = document.getElementById('cityInput').value;
      const apiKey = 'YOUR_API_KEY'; // Replace 'YOUR_API_KEY' with your actual API key from OpenWeatherMap
      const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${apiKey}`;

      fetch(apiUrl)
        .then(response => response.json())
        .then(data => {
          document.getElementById('city').textContent = data.name;
          document.getElementById('temperature').textContent = `Temperature: ${data.main.temp}°C`;
          document.getElementById('description').textContent = `Description: ${data.weather[0].description}`;
        })
        .catch(error => {
          console.log('Error fetching weather data:', error);
          alert('Unable to fetch weather. Please try again.');
        });
    }
  </script>
</body>
</html>
