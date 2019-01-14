<template>
    <div v-if="selectvideo" class="col-md-8">
        <div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" :src="videoURL" allowfullscreen></iframe>
        </div>
        <div class="details">
            <h4>{{ selectvideo.snippet.title }}</h4>
            <p>{{ selectvideo.snippet.description }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['selectvideo'],
    computed: {
        videoURL() {
            const {videoId} = this.selectvideo.id;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>

<style scoped>
.details {
    margin-top: 10px;
    margin-bottom: 10px;
    
    border: 1px solid #ddd;
    border-radius: 4px;

    padding-left: 5px;
    padding-right: 5px;
}
</style>
