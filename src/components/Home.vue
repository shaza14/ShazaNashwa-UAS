//home
<template>
  <div class="home-container">
    <div class="hero-section">
      <h1>Welcome To SHAZA-WIDGET</h1>
    </div>
    <div class="content">
      <!-- First row with 3 features -->
      <div class="feature-row">
        <ul>
          <li v-for="feature in features.slice(0, 3)" :key="feature.title" class="feature-item">
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
          </li>
        </ul>
      </div>

      <!-- Second row with 2 features -->
      <div class="feature-row">
        <ul>
          <li v-for="feature in features.slice(3)" :key="feature.title" class="feature-item">
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      features: [
        {
          title: 'WEATHER',
          description: 'This feature will display the weather for each city you are looking for'
        },
        {
          title: 'LOCATION',
          description: 'This feature will display the location of the users geolocation'
        },
        {
          title: 'STOPWATCH',
          description: 'This feature will display a timer'
        },
        {
          title: 'TIC TAC TOE',
          description: 'This feature will display the Tic Tac Toe game'
        },
        {
          title: 'PHOTO',
          description: 'This feature will display interesting photos that you choose'
        }
      ]
    };
  }
};
</script>
  
  <style>

.home-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-color: rgb(89, 178, 234);
    margin-top: 30px;
  }
  .hero-section {
  text-align: center;
  margin-bottom: 2rem;
  margin-top: 2rem;
  }
  .hero-section h1 {
  font-size: 3rem;
  color: rgb(26, 58, 135);
  text-transform: uppercase;
  letter-spacing: 2px;
}

.shaza-widget {
  color: #ffcc00;
  font-weight: bold;
}
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  .feature-item {
  margin-bottom: 1.5rem;
  padding: 1rem;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease-in-out;
}

.feature-item:hover {
  transform: scale(1.05);
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
}

.feature-item h3 {
  color: rgb(19, 42, 97);
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

.feature-item p {
  color: #fda50c;
  font-size: 1rem;
}
.content {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.feature-row {
  flex: 1;
  max-width: 300px;
  margin: 1rem;
}

/* Gaya tambahan untuk membuat kolom tombol Tic Tac Toe dan Photo berada di samping */
@media (max-width: 600px) {
  .feature-row {
    max-width: 100%;
  }
}
  </style>