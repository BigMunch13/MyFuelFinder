<template>
  <div class="map-container">
    <button @click="getCurrentUserLocation" class ="location-button">
      <img src="@/components/icons/LocationButton.png" alt="Location Icon" class="button-icon">
    </button>
  </div>
</template>

<script>
import gasIconUrl from '@/components/icons/GasIcon.png';
export default {
  data() {
    return {
      map: null,
      userLocationCircle: null
    }
  },

  mounted() {
    this.initializeMap();
    this.getCurrentUserLocation();
  },

  methods: {
    initializeMap() {
      this.map = L.map(document.querySelector('.map-container'), {
        attributionControl: false,
        zoomControl: false
      });

      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 20,
        attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
      }).addTo(this.map);

      L.control.zoom({
        position: 'bottomleft'
      }).addTo(this.map);

      L.control.scale({
        metric: true,
        imperial: false,
        position: 'bottomright'
      }).addTo(this.map);

      setTimeout(() => {
        this.map.invalidateSize();
      }, 5000);
    },

    getCurrentUserLocation() {
      if (!navigator.geolocation) {
        console.log("Geolocation is not supported by this browser.");
        this.setDefaultView();
      } else {
        // location tracking
        navigator.geolocation.getCurrentPosition(this.getPosition, this.locationError);
      }
    },
    getPosition(position) {
      var latitude = position.coords.latitude;
      var longitude = position.coords.longitude;
      var accuracy = position.coords.accuracy;

      this.map.setView([latitude, longitude], 14);

      //  Removing previus location
      if (this.userLocationCircle) {
        this.map.removeLayer(this.userLocationCircle);
      }

      // Adding new location
      this.userLocationCircle = L.circle([latitude, longitude], { radius: 30 }).addTo(this.map);
    },
    locationError(error) {
      console.log("Error while attempting to determine location:", error.message);
      this.setDefaultView();
    },

    setDefaultView() {
      this.map.setView([47.7819, 9.6136], 14);
    },
  },
  beforeUnmount() {
    // Aufräumen: Interval stoppen, wenn die Komponente entfernt wird
    if (this.locationUpdateInterval) {
      clearInterval(this.locationUpdateInterval);
    }
  }
}
</script>

<style>
.map-container {
  width: 100%;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
}

.location-button {
  position:absolute;
  bottom: 80px; 
  left: 10px;   
  z-index: 1000; 
  padding: 6px;
  background-color: white;
  border: solid #ccc; 
  cursor: pointer;
  display: flex;
  align-items: center;
}

.button-icon {
  width: 20px;  
  height: 20px; 
}
</style>