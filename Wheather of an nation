const apiKey = "9d04e7fff6ab4ae0684ae1d06f3386ff";
async function getWeather() {
    const city = document.getElementById("city").value;
    const weatherInfo = document.getElementById("weather-info");
    const errorMessage = document.getElementById("error-message");

    if (!city) {
        errorMessage.textContent = "Please enter a city name.";
        errorMessage.classList.remove("hidden");
        weatherInfo.classList.add("hidden");
        return;
    }

    try {
        const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`);
        const data = await response.json();

        if (data.cod !== 200) {
            throw new Error(data.message);
        }

        document.getElementById("city-name").textContent = data.name;
        document.getElementById("temperature").textContent = `Temperature: ${data.main.temp}°C`;
        document.getElementById("humidity").textContent = `Humidity: ${data.main.humidity}%`;
        document.getElementById("description").textContent = `Weather: ${data.weather[0].description}`;
        document.getElementById("weather-icon").src = `https://openweathermap.org/img/wn/${data.weather[0].icon}.png`;

        errorMessage.classList.add("hidden");
        weatherInfo.classList.remove("hidden");
    } catch (error) {
        errorMessage.textContent = error.message;
        errorMessage.classList.remove("hidden");
        weatherInfo.classList.add("hidden");
    }
}
