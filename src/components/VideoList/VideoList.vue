<template>
	<ul class="list-group">
		<VideoListItem 
			v-for='video in videos'
			:video='video'
			:key='video.etag'
			@videoSelected = 'onVideoSelect' >
			</VideoListItem>
	</ul>
	
</template>

<script> 
import VideoListItem from './VideoListItem/VideoListItem';

export default {
	name: 'VideoList',
	components: {
		VideoListItem
	},
	props: {
		videos: Array
	},
	methods: {
		onVideoSelect(video) {
			this.$emit('videoSelected', video);
		}
	}
}
</script>

<style scoped>

</style>
