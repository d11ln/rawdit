<template>
    <div>
        <div v-if="post.data.is_reddit_media_domain == false">
            <b-card :title="post.data.title" />
        </div>
        <div v-else-if="isVideo && (post.data.secure_media != null)">
            <b-card :title="post.data.title">
                <b-embed
                    type="video"
                    aspect="4by3"
                    controls
                    autoplay
                    muted
                    loop
                    poster
                >
                    <source
                        :src="post.data.secure_media.reddit_video.fallback_url"
                        type="video/mp4"
                    >
                </b-embed>
            </b-card>
        </div>

        <div v-else-if="isImage && (post.data.thumbnail != null)">
            <b-card
                :title="post.data.title"
                :img-src="post.data.url"
            />
        </div>
    </div>
</template>

<script>


export default {
    name: 'Posts',

    props: ['post',],
    methods: {
        isImage(url) {
            return url.match(/bmp|webp|png|jpg|jpeg|gif$/);
        },
        isVideo(post) {
            if (post.secure_media && post.secure_media.reddit_video)
                return post.url.match(/mp4|mkv|mov|gifv|webm$/);
        },

    },
};
</script>

<style >
.card {
  background-color: rgba(241, 241, 235, 0.829);
  margin-top:0.25rem;
  margin-bottom: 0.15rem;
}


</style>