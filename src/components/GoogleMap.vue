<template>
    <gmap-map class="gmap"
      :center="center"
      :zoom="11">
      <gmap-marker
        :key="index"
        v-for="(m, index) in markers"
        :position="m.position"
        @click="center=m.position">
      </gmap-marker>
    </gmap-map>
</template>

<script>
export default {
  name: "GoogleMap",
  data() {
    return {
      center: { lat: 39.7435, lng: -104.7080 },
      markers: [],
      places: [],
      currentPlace: null
    };
  },
  props: ["allEvents"],
  created(){
    // this.geolocate();
  },
  mounted() {
    this.createMarkersPerEvent(this.allEvents)
  },
  methods: {
    setPlace(place) {
      this.currentPlace = place;
    },
    addMarker() {
      if (this.currentPlace) {
        const marker = {
          lat: this.currentPlace.geometry.location.lat(),
          lng: this.currentPlace.geometry.location.lng()
        };
        this.markers.push({ position: marker });
        this.places.push(this.currentPlace);
        this.center = marker;
        this.currentPlace = null;
      }
    },
    geolocate: function() {
      navigator.geolocation.getCurrentPosition(position => {
        this.center = {
          lat: position.coords.latitude,
          lng: position.coords.longitude
        };
      });
    },
    createMarkersPerEvent(events) {
      events.map(event => {
        let positionObject = {}
        positionObject.position = {}
        positionObject.position.lat = event.lat
        positionObject.position.lng = event.long
        return this.markers.push(positionObject)
      })
    }
  }
};
</script>

<style>
.gmap {
  position: relative;
  width: 100vw;
  height: 89vh;
}
</style>