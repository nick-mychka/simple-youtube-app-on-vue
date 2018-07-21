<template>
  <div id="app" class = "container-fluid">
		<div class="row">
			<SearchBar 
				@termChange = 'onTermChange'
				msg = 'The simple app like YouTube on the Vue.js' />
		</div>
    <div class="row">
			<div class="col-12 col-lg-8">
				<VideoDetails :video = 'videoSelected' />
			</div>
			<div class="col-12 col-lg-4">
				<VideoList :videos="videos" @videoSelected = 'onVideoSelect' />
			</div>
		</div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar/SearchBar';
import VideoList from './components/VideoList/VideoList';
import VideoDetails from './components/VideoDetails/VideoDetails';

const API_KEY = 'AIzaSyAh1Wl3-Vp3RF3XxpUT0koy_SDHXQdd-Mk';

export default {
  name: 'app',
  components: {
		SearchBar,
		VideoList,
		VideoDetails
	},
	data() {
		return {
			videos: [],
			videoSelected: null
		}
	},
	methods: {
		onTermChange(searchTerm) {
			axios.get('https://www.googleapis.com/youtube/v3/search', {
				params: {
					key: API_KEY,
					type: 'video',
					part: 'snippet',
					q: searchTerm
				}
			}). then(response => {
				return this.videos = response.data.items;
			});
		},

		onVideoSelect(video) {
			this.videoSelected = video;
		}
	}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
