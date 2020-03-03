<template>
    <div class="col-md-4 pull-right">
        <ul class="list-group">
            <VideoListItem v-for="video in videos" :key="video.etag" :videoItem="video" @videoSelect="onVideoSelect"/>
        </ul>
        
    </div>
</template>

<script>
import VideoListItem from '@/components/VideoListItem'
export default {
    name:'VideoList',
    props:['videos'],
    components: {
        VideoListItem
    },
    methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect',video)
        }
    }

}
</script>

<style scoped>

</style>