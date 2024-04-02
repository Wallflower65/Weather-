<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="src/index.css" />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap"
      rel="stylesheet"
    />
    <link rel="stylesheet" href="src/style.css" />
    <script src="https://cdn.jsdelivr.net/npm/axios@1.1.2/dist/axios.min.js"></script>
    <title>Mozulu App</title>
  </head>
  <style>
    body {
      background-color: #f9f7fe;
      font-family: "Roboto", sans-serif;
    }

    a {
      color: #885df1;
    }

    .weather-app {
      background: white;
      max-width: 600px;
      margin: 45px auto;
      box-shadow: 0 30px 50px rgba(65, 50, 100, 0.08);
      border-radius: 16px;
      padding: 30px;
    }

    header {
      border-bottom: 1px solid #f9f7fe;
      padding: 0 0 30px 0;
    }

    .search-form-input {
      background-color: #f9f7fe;
      border: none;
      border-radius: 6px;
      width: 80%;
      font-size: 16px;
      padding: 15px 20px;
    }

    .search-form-button {
      background: #885df1;
      padding: 15px 30px;
      border: none;
      font-size: 16px;
      margin-left: 5px;
      border-radius: 6px;
      color: white;
    }

    main {
      padding: 30px 0;
    }

    .weather-app-data {
      display: flex;
      justify-content: space-between;
    }

    .weather-app-city {
      margin: 0;
      font-size: 38px;
      line-height: 48px;
    }

    .weather-app-details {
      font-size: 16px;
      color: rgba(39, 33, 66, 0.4);
      line-height: 24px;
      font-weight: 500;
    }

    .weather-app-details strong {
      color: #f65282;
    }

    .weather-app-temperature-container {
      display: flex;
    }

    .weather-app-icon {
      font-size: 44px;
      margin-top: 22px;
    }

    .weather-app-temperature {
      font-size: 88px;
      margin-left: 10px;
      font-weight: bold;
    }

    .weather-app-unit {
      margin-top: 16px;
      font-size: 28px;
    }

    footer {
      border-top: 1px solid #f9f7fe;
      padding: 30px 0 0 0;
      text-align: center;
      font-size: 14px;
      color: rgba(0, 0, 0, 0.6);
    }

  </style>
  <body>
    <h1>Welcome to the Mozulu App</h1>
    <div class="weather-app">
      <header>
        <form class="search-form" id="search-form">
          <input
            type="search"
            placeholder="Enter a city.."
            required
            id="search-form-input"
            class="search-form-input"
          />
          <input type="submit" value="Search" class="search-form-button" />
        </form>
      </header>
      <main>
        <div class="weather-app-data">
          <div>
            <h1 class="weather-app-city" id="city"></h1>
            <p class="weather-app-details">
              <span id="time"></span>,
              <span id="description"></span>
              <br />
              Humidity: <strong id="humidity"></strong>, Wind:
              <strong id="wind-speed"></strong>
            </p>
          </div>
          <div class="weather-app-temperature-container">
            <div id="icon"></div>
            <div class="weather-app-temperature" id="temperature"></div>
            <div class="weatehr-app-unit">°C</div>
          </div>
        </div>
      </main>

      <footer>
        This project was coded by
        <a href="https://github.com/Wallflower65" target="_blank">
          Phaphamani Zoneleni</a
        >, is open-sourced on
        <a href="https://github.com/Wallflower65/Weather-" target="_blank"
          >GitHub</a
        >
      </footer>
    </div>
    <script src="src/index.js"></script>
    <script>
      function refreshWeather(response) {
        console.log(response.data);
      }

      function searchCity(city) {
        let apiKey = "787ofe478b86fc75394a34e4469a2t40";
        let apiUrl =
          "https://api.shecodes.io/weather/v1/forecast?query=${city}&key=${apiKey}&units=metric";
        axios.get(apiUrl).then(refreshWeather);
      }

      function handleSearchSubmit(event) {
        event.preventDefault();
        let searchInput = document.querySelector("#search-form-input");
        let cityElement = document.querySelector("#city");
        cityElement.innerHTML = searchInput.value;
        searchCity(searchInput.value);
      }

      let searchFormElement = document.querySelector("#search-form");
      searchFormElement.addEventListener("submit", handleSearchSubmit);
    </script>

  </body>
</html>
