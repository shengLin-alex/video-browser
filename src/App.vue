<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row">
            <VideoDetail :selectedVideo="selectedVideo"></VideoDetail>
            <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
        </div>
    </div>
</template>

<script type="text/javascript">

    import axios from 'axios';
    import SearchBar from './components/SearchBar';
    import VideoList from './components/VideoList';
    import VideoDetail from './components/VideoDetail';

    // YOUTUBE API KEY
    const API_KEY = process.env.VUE_APP_YOUTUBE_APIKEY;

    export default {
        name: 'App',
        components: {
            SearchBar,
            VideoList,
            VideoDetail
        },
        // vue component 的 data 必須是 function return obj
        data() {
            return {
                videos: [],
                selectedVideo: null
            };
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
                }).then(res => {
                    this.videos = res.data.items;
                });
            },

            onVideoSelect(video) {
                this.selectedVideo = video;
            }
        }
    };

</script>