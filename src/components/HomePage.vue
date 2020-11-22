<template>
    <div class="mainBody">
        <Header />
        <b-container>
            <div
                v-for="post in posts"
                :key="post.id"
            >
                <b-card
                    :title="post.data.subreddit"
                    :footer="`👆 ${post.data.ups} 👇${post.data.downs} 🏆${post.data.gilded} 🗣${post.data.num_comments}`"
                >
                    <Posts :post="post" />
                </b-card>
            </div>
        </b-container>
    </div>
</template>

<script>
import Header from './Header';
import Posts from './Posts';

export default {
    name: 'HomePage',
    components: {
        Posts,
        Header,
    },
    props: ['posts',],

};
</script>

<style scoped>
.mainBody {
 background:#3e3e3e
}

</style>
