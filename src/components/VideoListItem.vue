<template>
    <li class="list-group-item media" @click="onVideoSelect">
        <img class="mr-3" :src="thumbnailUrl" alt="video_thumbnail">
        <div class="media-body">
            {{videoItem.snippet.title}}
        </div>
    </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['videoItem'],
    computed: {
        thumbnailUrl() {
            return this.videoItem.snippet.thumbnails.default.url
        }
    },
    methods: {
        onVideoSelect() {
            this.$emit('videoSelect', this.videoItem)
        }
    }
}
</script>

<style scoped>
li {
    display: flex;
    cursor: pointer;
}

li:hover {
    background-color: #eee
}
</style>