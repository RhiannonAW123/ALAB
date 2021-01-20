<template>
  <div id='app'>
   hello world 
 <bookings-grid v-bind:bookings="bookings"> </bookings-grid>
 <booking-form> </booking-form>
</div>
  
</template>

<script>
import { eventBus } from './main.js';
import BookingForm from '@/components/BookingForm';
import BookingsGrid from '@/components/BookingsGrid';
import BookingsService from './services/BookingsService';


export default {
  name: 'app',
  components: {
    'booking-form': BookingForm,
    'bookings-grid': BookingsGrid
  },
  data() {
    return {
      bookings: []
    };
  },
  mounted() {
    this.fetchBookings();

    eventBus.$on('added-booking', payload => {
      BookingService.postBookings(payload)
      .then(booking => this.bookings.push(booking));
    });

    eventBus.$on('delete-booking', id => {
      BookingService.deleteBooking(id)
      .then(() => {
        const index = this.bookings.findIndex(booking => booking._id === id );
        this.bookings.splice(index, 1);
      });
    });
  },
  methods: {
    fetchBookings() {
      BookingsService.getBookings()
      .then(bookings => this.bookings = bookings);
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,100&display=swap');
body {
  font-size: 14px;
  font-family: Sans-Serif;
}
* {
  box-sizing: border-box;
}
a {
  text-decoration: none;
}

.Img > div {
  position: fixed;
  width: 100%;
  height: 440px;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
}


header {
  position: absolute;
  top: 0;
  width: 100%;
  padding: 0px 20px;
}
header > div {
  max-width: 600px;
  margin: 0 auto;
  padding-top: 150px;
  height: 380px;
  text-align: center;
  color: White;
}

header p {
  font-size: 2em;
  margin-bottom: 0.7em;
  font-family: 'Montserrat', sans-serif;
}
h1 {
  font-weight: 600;
  font-size: 3.4em;
  margin-bottom: 0.2em;
}
nav {
  max-width: 600px;
  margin: 0 auto;
  height: 60px;
  border-top: 2px rgba(255, 255, 255, 0.308) solid;
}
nav ul li {
  display: inline-block;
  margin-right: 35px;
}
nav ul li a {
  font-weight: 800;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  color: rgba(255, 255, 255, 0.308);
  display: block;
}
nav ul li a.active {
  box-shadow: 0px -1px 0px #fff;
}
nav ul li a.active,
nav ul li a:hover {
  color: #fff;
}
</style>
