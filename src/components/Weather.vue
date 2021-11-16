<template>
	<div class="container">
		<h1 class="text-center my-5">Weather with Vue.js</h1>
		<div class="mb-3">
			<label for="location" class="form-label">Search city</label>
			<input type="text" class="form-control" id="location" @keypress.enter="setWeather" v-model="request" ref="focusInput">
		</div>
		<div class="w-75 m-auto" v-if="weather">
			<h3 class="text-center my-5">Location: {{ weather.name }}</h3>
			<div class="card text-center p-4 rounded-3">
				<p class="txt">Temperature: <strong>{{ weather.main.temp.toFixed() }}°</strong></p>
				<p class="txt">Weather: {{ weather.weather[0].description }}</p>
			</div>
		</div>
	</div>
</template>

<script>

import axios from 'axios'

export default {
	name: 'Weather',
	data() {
		return {
			weather : undefined,
			request: '',
			api_key: process.env.VUE_APP_API_KEY,
			url: 'https://api.openweathermap.org/data/2.5/weather?'
		}
	},
	methods: {
		focus : function () {
			this.$refs.focusInput.focus();
		},
		setWeather : function () {
			if (this.request !== '')
			{
				axios
				.get(`${this.url}q=${this.request}&units=metric&appid=${this.api_key}`)
				.then(response => {
					this.weather = response.data;
				})
				this.request = ''
			}
		}
	},
	mounted () {
		this.focus();
	}
}

</script>

<style scoped>

.txt {
	font-size: 25px;
	font-weight: 300;
}

</style>
