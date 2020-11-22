<template>
    <div id="app">
        <HomePage
            :posts="myData"
        />
    </div>
</template>

<script>
import HomePage from './components/HomePage.vue';
import axios from 'axios';

Window.axios = require('axios');
export default {
    name: 'App',
    components: {
        HomePage,
    },

    data () {
        return {
            myData: {},
        };
    },
    mounted () {
        axios
            .get('https://reddit.com/.json')
            .then(res => this.myData = res.data.data.children)
            .catch(err => console.log(err));
    },


};

</script>