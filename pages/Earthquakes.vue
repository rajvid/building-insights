<template>
  <div>
    <Navbar />
    <!--Created full width container with class b-container-fluid-->
    <b-container fluid class="bv-example-row">
      <b-row class="my-md-3">
        <b-col md="6" offset-md="1" offset-lg="2" class="text-uppercase font-italic">
        <!--Section Heading-->
        <h1>Earthquake Activity > M6.0</h1>
        </b-col>
        <!--Adding w-100 class to force next columns to break to new line-->
        <div class="w-100"></div>
        <!--Lopping through the extracted data for earthquakes-->
        <b-col
        md="10"
        offset-md="1"
        lg="8"
        offset-lg="2"
        class="container"
        v-if="earthquakes">
          <!--Utilizing card to loop through the list of earthquakes and display on page-->
          <card
          v-for="earthquake of earthquakes.features"
          :key="earthquake.id"
          :earthquake="earthquake"
          />
        </b-col>
      </b-row>
    </b-container>
    <Footer />
  </div>
</template>

<script>
// Importing the portfolio image component here
import axios from 'axios'
import Card from '../components/EarthquakeCard.vue'

export default {
  components: {
    Card
  },
  name: 'EarthquakesPage',
  data () {
    return {
      title: 'Building Insights : Earthquakes',
      loading: true,
      earthquakes: null,
      errored: false
    }
  },
  mounted () {
    axios
      // Utilizing USGS web api link to get the most recent earthquakes with magnitude greater than 7.0
      .get('https://earthquake.usgs.gov/fdsnws/event/1/query?format=geojson&starttime=2010-01-01&minmagnitude=6&limit=5')
      .then(response => (this.earthquakes = response.data))
      // if error then it will console log error
      .catch((error) => {
        console.log(error)
        this.errored = true
      })
      // finally loding state moves to false
      .finally(this.loading = false)
  },
  head () {
    return {
      title: this.title,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'Structural Engineering',
          name: 'Structural Engineering',
          content: 'Structural Engineering and Seismic Engineering Blog'
        }
      ]
    }
  }
}
</script>

<style scoped lang="scss">

// Importing partials here
@import '@/assets/styles/_base.normalize.scss';
@import '@/assets/styles/_components.content.scss';
@import '@/assets/styles/_settings.responsive.scss';
@import '@/assets/styles/_settings.variables.scss';

// Added style to H1 text Featured Project
h1 {
  font-weight: 100;
  font-style: italic;
  font-size: 3.2em;
  line-height: 1.2;
  // Added margin top-bottom  and changed font size for small screen
  @include media-query("mobile") {
    font-size: 2.1em;
    margin: 1rem 0;
  }
  @include media-query("lg") {
    font-size: 4.2em;
    margin: 2rem 0;
  }
}
</style>
