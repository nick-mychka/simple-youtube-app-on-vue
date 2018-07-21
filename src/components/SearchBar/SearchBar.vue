<template>
  <div class="col">
		<div class="title"> {{ msg }} </div>
		<input type="text" placeholder="Search video ..." @input = 'onInput' />
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  props: {
    msg: String
	},
	methods: {
		onInput(event) {
			this.$emit('termChange', event.target.value)
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	input {
		width: 50%;
		height: 50px;
		padding: 15px;
		font-size: 18px;
		outline: 0;
	}

	div {
		text-align: center;
		margin: 20px auto;
	}
	.title {
		width: 75%;
		padding: 7px;
		margin-top: 0px;
		color: #fff;
		font-size: 20px;
		text-transform: uppercase;
		background-color: #ff0000;
		border-radius: 7px;
	}
</style>
