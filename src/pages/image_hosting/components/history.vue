<script setup>
import { ref } from 'vue';
import * as file from '@/api/files'
import { handleClickImg } from './utils';

const files = ref([])
const baseURL = 'http://hw:5000/file'

async function render(){
    const ret = await file.getList()
    files.value = ret.data
}

render()
</script>

<template>
    <v-card>
        <div id="con">
            <v-img v-for="item in files" :src="`${baseURL}/${item.id}`" @click="handleClickImg(baseURL.concat('/').concat(item.id))" class="hover:cursor-pointer"></v-img>
        </div>
    </v-card>
</template>

<style scoped>
#con {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
}
</style>