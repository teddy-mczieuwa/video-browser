<template>
  <div>
    <SearchBar @termChange="onTermChange"/>
    <div class="row">
    <VideoDetails :video="selectedVideo"/>
    <VideoList @videoSelect="onVideoSelect" :videos="videos"/>
    </div>
   
  </div>
</template>

<script>
import axios from 'axios'
// @ is an alias to /src
import SearchBar from '@/components/SearchBar.vue'
import VideoList from '@/components/VideoList.vue'
import VideoDetails from '@/components/VideoDetails.vue'
const API_KEY = 'AIzaSyAQV3cOrlpjmPkivLdD1gswS7UIvwa6658'

export default {
  name: 'Home',
  components: {
    SearchBar, VideoList, VideoDetails
  },
  data() {
    return {
      videos: Array(),
      selectedVideo: null
    }
  },
  methods: {
    async onTermChange(payload) {
      try {
        const res = await axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: payload
          }
        })
        console.log(res)
        this.videos = res.data.items
      } catch (error) {
        console.log(error)
      }
      
    },

    onVideoSelect(video) {
      console.log(video.snippet.title)
      this.selectedVideo = video
    }
  }
}
</script>
