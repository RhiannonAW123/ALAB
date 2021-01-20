<template lang='html'>
<div>
    <h3>{{ booking.name }}</h3>
    <p>email: {{ booking.email }}</p>
    <p>checkInStatus: {{ booking.checkInStatus }}</p>
    <button v-on:click="handleDelete">Delete Booking</button>
</div>
</template>

<script>
import { eventBus} from '@/main.js'

export default {
    name: 'bookings-card',
    props: ['booking'],
    methods: {
    handleDelete: function() {
      eventBus.$emit('delete-booking', this.booking._id);
    }
    }
}
</script>