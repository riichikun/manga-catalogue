<template>
    <main class="title__page">
        <div className="link__container">
            <a href="/">Back to homepage</a>
        </div>
        <section className="title__section">
                <div class="title-pic__block">
                    <h1>{{title.title}}</h1>
                    <img :src="title.images?.jpg.large_image_url" :alt="title.title">
                </div>
                <p>{{title.synopsis}}</p>
        </section>
    </main>
</template>

<script lang="ts">
import axios from 'axios';


    export default {
        data() {
            return ({
                title: {} as any,
            })
        },
        methods: {
            getApi(url: string) {
                axios.get(url).then((e) => {this.title = e.data.data})
    }
        },
        mounted() {
            let id = this.$router.currentRoute.value.params.id;
            this.getApi(`https://api.jikan.moe/v4/manga/${id}/full`)
        }
    }
</script>