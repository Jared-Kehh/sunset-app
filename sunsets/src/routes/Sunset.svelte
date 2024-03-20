<script>
    import { writable } from 'svelte/store';

const sunsetTime = writable(null);

// Fetch sunset time data from OpenWeatherMap API
async function fetchSunsetTime() {
  const apiKey = '13ab5a66f99f190dc9cdc5906e24c2bb';
  const city = 'Rexburg';
  const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}`);
  const data = await response.json();
  sunsetTime.set(data.sys.sunset);
}

fetchSunsetTime(); // Fetch the sunset time when the component is mounted

// Helper function to format the sunset time
function formatSunsetTime(unixTimestamp) {
  const date = new Date(unixTimestamp * 1000);
  return date.toLocaleTimeString();
}


    fetch('https://api.openweathermap.org/data/2.5/weather?lat=43.82&lon=-111.79&appid=13ab5a66f99f190dc9cdc5906e24c2bb')
  .then(response => {
    // Check if the response is successful
    // Parse the JSON data returned by the API
    return response.json();
  })
  .then(data => {
    // Work with the JSON data here
    console.log(data);
    const weather = document.getElementById("temp");
    weather.innerHTML = `<img src="https://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png">
    <h2>Location: ${data.name}</h2>
    <p>${Math.round((data.main.temp - 273.15) * 9/5 + 32)}°F 
    - ${data.weather[0].main}</p>`
  })
  .catch(error => {
    // Handle any errors that occurred during the fetch
    console.error('There was a problem with the fetch operation:', error);
  });
</script>
<main>
    <h1>Congrats you got the BOOTY!</h1>
    <div class="sunset" id="temp"></div>
    <div>
      {#if $sunsetTime}
        <p>Sunset Time: {formatSunsetTime($sunsetTime)}</p>
      {:else}
        <p>Loading...</p>
      {/if}
    </div>
</main>

<style>
    main{
      background-image: url("https://images.pexels.com/photos/5006585/pexels-photo-5006585.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1");
      width: 100%;
      height: 100%;
      background-repeat: no-repeat;
      background-position: center;
      display: flex;
      flex-direction: column;
      background-size: cover;
      justify-content: center;
      align-items: center;
    }
    h1{
      position: relative;
    }
    button{
      position: relative;
      width: 200px;
    }
  </style>