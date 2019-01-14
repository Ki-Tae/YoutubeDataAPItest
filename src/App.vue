<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row">
            <VideoDetail
            :selectvideo="selectedVideo"
            >
            </VideoDetail>
            <VideoList
            :videos="videos"
            @videoSelect="onvideoSelect"
            >
            </VideoList>   
        </div>
        
    </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const API_KEY = 'AIzaSyCe6xGeIWsMKu7luJp3Cai54CNX1nc3bsE';

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList,
        VideoDetail
    },
    data() {
        return {videos: [], selectedVideo: null };
    },
    methods: {
         onTermChange(searchTerm) {

            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet', // little info for every video that is returned
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items;
            });
        
        },
        onvideoSelect(video) {
            this.selectedVideo = video;
        },
    }
};
</script>
