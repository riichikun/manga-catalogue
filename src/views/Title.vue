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
        <section>
            <h1>Read {{title.title}}</h1>
            <div class="volumes__block">
                <div class="volume">
                    <button @click="toggleChapters">Volume 1</button>
                    <div class="volume__inner">
                        <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                </div>
                <div class="volume">
                    <button @click="toggleChapters">Volume 2</button>
                    <div class="volume__inner">
                       <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                </div>
                <div class="volume">
                    <button @click="toggleChapters">Volume 3</button>
                    <div class="volume__inner">
                       <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                </div>
                <div class="volume">
                    <button @click="toggleChapters">Volume 4</button>
                    <div class="volume__inner">
                       <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                </div>
                <div class="volume">
                    <button @click="toggleChapters">Volume 5</button>
                    <div class="volume__inner">
                       <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                </div>
                <div class="volume">
                    <button @click="toggleChapters">Volume 6</button>
                    <div class="volume__inner">
                       <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                </div>
                <div class="volume">
                    <button @click="toggleChapters">Volume 7</button>
                    <div class="volume__inner">
                       <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                 </div>
                <div class="volume">
                    <button @click="toggleChapters">Volume 8</button>
                    <div class="volume__inner">
                       <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                 </div>
                <div class="volume">
                    <button @click="toggleChapters">Volume 9</button>
                    <div class="volume__inner">
                       <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                </div>
                <div class="volume">
                    <button @click="toggleChapters">Volume 10</button>
                    <div class="volume__inner">
                       <button @click="openChapter" class="chapter">1</button>
                       <button @click="openChapter" class="chapter">2</button>
                       <button @click="openChapter" class="chapter">3</button>
                       <button @click="openChapter" class="chapter">4</button>
                       <button @click="openChapter" class="chapter">5</button>
                    </div>
                </div>
            </div>        
            <div class="content__block">
                <div className="manga-content">
                    There could be {{title.title}} volume {{ currentVol }} chapter {{ currentChapter }} page {{ currentPage }}
                    <div class="page-turner">
                        <div @click="turnPage($event, 'prev')" class="prev"></div>
                        <div @click="turnPage($event, 'next')" class="next"></div>
                    </div>
                </div>
                
                <div class="manga__nav">
                    <button @click="openPage">1</button>
                    <button @click="openPage">2</button>
                    <button @click="openPage">3</button>
                    <button @click="openPage">4</button>
                    <button @click="openPage">5</button>
                    <button @click="openPage">6</button>
                    <button @click="openPage">7</button>
                    <button @click="openPage">8</button>
                    <button @click="openPage">9</button>
                    <button @click="openPage">10</button>
                </div>
            </div>
        </section>
        </main>
</template>

<script lang="ts">
import axios from 'axios';


    export default {
        data() {
            return ({
                title: {} as any,
                currentVol: 1 as number,
                currentChapter: 1 as number,
                currentPage: 1 as number,
            })
        },
        methods: {
            getApi(url: string) {
                axios.get(url).then((e) => {this.title = e.data.data})
            },
            toggleChapters(e: any) {
                e.target.nextElementSibling.style.display = e.target.nextElementSibling.style.display == 'flex' ?  'none' : 'flex';
                this.currentPage = 1
            },
            openChapter(e: any) {
                this.currentChapter = Number(e.target.innerText);
                console.log(e.target.parentElement.previousElementSibling.innerText)
                this.currentVol = e.target.parentElement.previousElementSibling.innerText.replace('Value ', '')
                const contentBlock = document.querySelector<HTMLElement>('.content__block')!
                contentBlock.style.display = 'flex';
            },
            openPage(e: any) {
                this.currentPage = Number(e.target.innerText);
            },
            turnPage(e: any, direction: string) {
                if(direction=='prev') {
                    if(this.currentPage == 1) {
                        if(this.currentChapter == 1) {
                            if(this.currentVol == 1) {
                                return
                            }
                            else {
                                this.currentVol -= 1
                                this.currentChapter = 5
                                this.currentPage = 10
                            }
                        }
                        else {
                            this.currentChapter -= 1
                            this.currentPage = 10

                        }
                    }
                    else this.currentPage -= 1
                }
                else if(direction='next') {
                    if(this.currentPage == 10) {
                        if(this.currentChapter == 5) {
                            if(this.currentVol == 10) {
                                return
                            }
                            else {
                                this.currentVol += 1
                                this.currentChapter = 1
                                this.currentPage = 1

                            }
                        }
                        else {
                            this.currentChapter += 1
                            this.currentPage = 1
                        }
                    }
                    else this.currentPage += 1
                }

            }
        },
        mounted() {
            let id = this.$router.currentRoute.value.params.id;
            this.getApi(`https://api.jikan.moe/v4/manga/${id}/full`)
        }
    }
</script>