<script>
    let gender = "";
    let name = "";
    async function getGender() {
      fetch('https://api.genderize.io/?name=' + name)
        .then((response) => response.json())
        .then((data) => {
          //Able to change whatever name you like Example: weatherTemparature = data.temperature the name of data should not be changed.
          name = data.name; // Path for name
          gender = data.gender; // Path for gender
        });
    }
        </script>
        <h1>Guess Your Gender 🤔</h1>

        <form on:submit|preventDefault={getGender}>    
            <label for="location">Name:</label>
            <input id="location" bind:value={name} type="text" />
            <button type="submit">Check</button>
        </form>
        <p>Gender: {gender}</p>