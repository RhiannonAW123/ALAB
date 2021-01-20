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
		
		<input type="submit" value="Save" id="save"/>
	</form>
</template>

<script>
import { eventBus } from '@/main.js';

export default {
	name: 'bookings-form',
	data() {
		return {
			fullName: '',
			email: '',
			checkInStatus: ''
		
		}
	},

methods: {
	handleSubmit() {
		const payload = {
			fullName: this.fullName,
			email: this.email,
		};

		eventBus.$emit('added-booking', payload);
		this.fullName = '';
		this.email ='';
	}

}
}
</script>