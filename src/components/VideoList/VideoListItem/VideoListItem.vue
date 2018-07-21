<template>
	<li class="list-group-item media"
		@click = 'onVideoSelect' >
		<img class="mr-3" :src="thumbnailsUrl" alt="Youtube">
		<div class="media-body">
			{{video.snippet.title}}
		</div>
	</li>
</template>

<script>
export default {
	name: 'VideoListItem',
	props: ['video'],
	computed: {
		thumbnailsUrl() {
			return this.video.snippet.thumbnails.default.url;
		}
	},
	methods: {
		onVideoSelect() {
			this.$emit('videoSelected', this.video);
		}
	}
}
</script>

<style scoped>
	li {
		display: flex;
		cursor: pointer;
		text-align: left;
		transition: background-color 0.15s ease-in-out;
	}
	li:hover {
		background-color: #eee;
	}	
</style>