<template>
    <div v-if="selectedVideo">
        {{ selectedVideo.snippet.title }}
    </div>
</template>

<script>
    export default {
        name: 'VideoDetail',
        props: ['selectedVideo']
    }
</script>