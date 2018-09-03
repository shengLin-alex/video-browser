<template>
    <div v-if="selectedVideo" class="col-md-8">
        <div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" :src="videoUrl" frameborder="0" allowfullscreen></iframe>
        </div>
        <div class="details">
            <h4>{{ selectedVideo.snippet.title }}</h4>
            <p>{{ selectedVideo.snippet.description }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'VideoDetail',
        props: ['selectedVideo'],
        computed: {
            videoUrl() {

                return `https://www.youtube.com/embed/${ this.selectedVideo.id.videoId }`;
            }
        }
    }
</script>

<style scoped>
    .details {
        margin-top: 10px;
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 4px;
    }
</style>