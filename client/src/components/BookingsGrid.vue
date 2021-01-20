<template lang='html'>
    <div id="bookingsGrid">         
    <bookings-card v-for="(booking, index) in bookings" :key="index" :booking="booking" />
    </div>
</template>

<script>
import BookingsCard from './BookingsCard';

export default {
    name: 'bookings-grid',
    components: {
        'bookings': Bookings
    },
    props: ['bookings']

}


</script>