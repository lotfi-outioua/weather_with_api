<template>
	<div id="app">
		<weather></weather>
	</div>
</template>

<script>

import Weather from './components/Weather'

export default {
	name: 'App',
	components: {
		weather : Weather
	}
}

</script>

<style>

body {
	background: radial-gradient(circle, hsla(221, 45%, 73%, 1) 0%, hsla(152, 77%, 77%, 0.5) 0%, hsla(164, 35%, 19%, 1) 100%);
}

#app {
	font-family: sans-serif;
	color: #003049;
}

</style>