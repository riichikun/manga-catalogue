

<template lang="">
    <main>
        <section className='search__block'>
            <h1>Search for any manga you want</h1>
            <form @submit.prevent="getTitles" action="">
                <input type="search" placeholder="Search" name="search">
                <label for="select">Choose a genre if needed:</label>
                <select v-model ="selectedGenre" name="select">
                    <option value="All" selected>All</option>
                    <option value="Action">Action</option>
                    <option value="Adventure">Adventure</option>
                    <option value="Comedy">Comedy</option>
                    <option value="Drama">Drama</option>
                    <option value="Fantasy">Fantasy</option>
                </select>
                <input  type="submit" value="Search">
            </form>

        </section>
        <section className="title-cards">
            <div v-for="title in titles" className="title-card">
                <a :href='"/title/" + title.mal_id'>{{title.title}}</a>
                <a :href='"/title/" + title.mal_id' href=""><img :src="title.images.jpg.image_url" alt=""></a>
                <p>{{title.synopsis}}</p>
    
            </div>
          
        </section>
    </main>
</template>

<script lang="ts">
import axios from 'axios';
import {ref} from 'vue';

export default {
    data() {
    return {
      titles: [] as Array<any>,
    genres: {
        Action: 1,
        Adventure: 2,
        Comedy: 4,
        Drama: 8,
        Fantasy: 10
    },
    selectedGenre: ref("All")
    }
  },
  methods: {
    getTitles(form: any) {
        if(form.target.elements.search.value) {
            if(this.selectedGenre == "All") {
                console.log(1)
                this.titles = [];
                axios.get(`https://api.jikan.moe/v4/manga?q=${form.target.elements.search.value}&sfw&genres_exclude=28,26`).then((e) => {
                this.titles = e.data.data
                }).then((e) => {
                    for(let i = 0; i<this.titles.length; i++) {
                        if(this.titles[i].synopsis) this.titles[i].synopsis = this.titles[i].synopsis.slice(0, 300) + '...';
                    }
                    })
            }
            else {
                console.log(2)
                this.titles = [];
                console.log(`https://api.jikan.moe/v4/manga?q=${form.target.elements.search.value}&sfw&genres_exclude=28,26?genres=${this.genres[this.selectedGenre]}`)
                axios.get(`https://api.jikan.moe/v4/manga?q=${form.target.elements.search.value}&sfw&genres_exclude=28,26&genres=${this.genres[this.selectedGenre]}`).then((e) => {
                this.titles = e.data.data
                }).then((e) => {
                    for(let i = 0; i<this.titles.length; i++) {
                        if(this.titles[i].synopsis) this.titles[i].synopsis = this.titles[i].synopsis.slice(0, 300) + '...';
                    }
                    })
            }
           
        }
        else if(this.selectedGenre == "All") {
            this.getApi('https://api.jikan.moe/v4/top/manga')
        }
        else {
            this.getApi(`https://api.jikan.moe/v4/manga?genres=${this.genres[this.selectedGenre]}`)
        }
    },
    getApi(url: string) {
        axios.get(url).then((e) => {this.titles = e.data.data}).then((e) => {
                for(let i = 0; i<this.titles.length; i++) {
                    if(this.titles[i].synopsis) this.titles[i].synopsis = this.titles[i].synopsis.slice(0, 300) + '...';
                }
            })
    }
  },
  mounted() {
    this.getApi('https://api.jikan.moe/v4/top/manga');
  },
}
</script>
<style lang="">
    
</style>