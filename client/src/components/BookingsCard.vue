<template lang='html'>
<div>
    <h3>{{ booking.name }}</h3>
    <p>email: {{ booking.email }}</p>
    <p>checkInStatus: {{ booking.checkInStatus }}</p>
    <!-- <button v-on:click="handleDelete(booking._id)">Delete Booking</button> -->
</div>
</template>

<script>
import { eventBus} from '@/main.js'

export default {
    name: 'bookings-card',
    props: ['booking'],
    methods: {
    // handleDelete(id) {
    //   eventBus.$emit('delete-booking', id);
    // }
    }
}
</script>