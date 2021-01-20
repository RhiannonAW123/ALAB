<template lang="html">
	<form id="bookings-form" v-on:submit.prevent="handleSubmit">
		<h2>Add a Booking</h2>
		<div class="formWrap">
			<label for="fullName">fullName:</label>
			<input type="text" id="fullName" v-model="fullName" />
		</div>
       
         <div class="formWrap">
			<label for="email">email:</label>
			<input type="text" id="email" v-model="email" />
		</div>
		
    <label for="checkInStatus">Checked In:</label>
    <input type="checkbox" id="checkInStatus" name="checkInStatus">

		<input type="submit" value="Save" id="save"/>
	</form>
</template>

<script>
import { eventBus } from '@/main.js';


export default {
	name: 'booking-form',
	data() {
		return {
			fullName: '',
			email: '',
			checkInStatus: false
		
		}
	},

methods: {
	handleSubmit() {
		const booking = {
			name: this.fullName,
			email: this.email,
			checkInStatus: this.checkInStatus
		}
	
	eventBus.$emit('addBooking', booking)
	}

}
}
</script>