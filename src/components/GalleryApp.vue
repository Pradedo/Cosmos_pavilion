<template>
    <div ip="vie-slider">
        <h1 align="center">Фото</h1>
        <hr>
        <div align="center" class="picture">
            <img :src="activePic">
        </div>
        <div class="pictures">
        <div v-for="(picture, index) in pictures" v-bind:key="index">
            <img :src="picture" @mouseover="changeActivePic(index)" class="active">
        </div>
    </div>
    </div>
</template>
<script>
export default{
            data() {
              return {
                activePic: 'img/file_1.jpg',
                pictures: [
                    'img/file_1.jpg',
                    'img/file_2.jpg',
                    'img/file_3.jpg',
                    'img/file_4.jpg',
                    'img/file_5.jpeg',
                    'img/file_6.jpeg',
                    'img/file_7.jpg'
                ]
              }
            },
            methods: {
                changeActivePic(index){
                    this.activePic = this.pictures[index];
                }
            }
        }
</script>