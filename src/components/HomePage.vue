<script setup lang="ts">
import type { ThreadI, PostI } from '@/data/data.interfaces'
import sourceData from '@/data/data.json'
import { ref } from 'vue';

const threads = ref<ThreadI[]>(sourceData.threads)
const posts = ref<PostI[]>(sourceData.posts)
</script>

<template>
    <h1>Threads</h1>
    <div v-for="thread in threads" :key="thread.id">
        <h2>{{ thread.title }}</h2>
        <div v-for="postId in thread.posts" :key="postId">
            <p>{{ posts.find(x => x.id === postId)?.text }}</p>
        </div>
    </div>
</template>