<template>
    <div id="app">
        <div class="container">
            <h1 class="title"> Playlist </h1>
            <hr />
            <form class="form-inline" @submit.prevent ="addSong">
                <input type="text" placeholder="Artist" class="form-control" v-model="newSong.artist" />
                <input type="text" placeholder="Title" class="form-control" v-model="newSong.title" />
                <button type="submit" class="btn-btn-primary">Add</button>
            </form>
            <br />
            <ul class="songlist">
                <song
                    v-for="song in songs"
                    :key="song.id">
                    <button type="button" class="btn" :class="{'btn-warning' : song.favorite }" @click="toggleFavorite(index)">Fav</button>
                    {{ song.artist }} - {{ song.title }}
                    <button type="button" class="btn btn-danger" @click="deleteSong(index)">X</button>
                </song>

            </ul>
        </div>
    </div>
</template>

<script>
    import Song from './Song.vue'

    export default {
        components: { Song },

        methods: {
            addSong () {
                this.songs.splice(0,0, { title: this.newSong.title, artist: this.newSong.artist });
                this.newSong = { title: '', artist: ''}
            },
            deleteSong(target) {
                this.songs.splice(target, 1)
            },
            toggleFavorite(target) {
                this.songs[target].favorite = !this.songs[target].favorite;
            }
        },

        data() {
            return {
                songs: [
                    { id: 1, title: 'Roar', artist: 'Katy Perry'},
                    { id: 2, title: 'Leroy Brown', artist: 'Jim Croce' },
                    { id: 4, title: 'The Power of Love', artist: 'Celine Dion'}
                ],

                newSong: {
                    title: '',
                    artist: ''
                }
            }
        }
}
</script>

<style lang="css" scoped>
    .songlist {
        margin: 1rem;
        padding: 1rem;
        border: 1px solid black;
        list-style: none;
    }
</style>
