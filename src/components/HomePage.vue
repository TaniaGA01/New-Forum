<script setup lang="ts">
import type { ThreadI, PostI, UserI } from '../data/data.interfaces'
import sourceData from '../data/data.json'
import { ref } from 'vue';

const threads = ref<ThreadI[]>(sourceData.threads)
const posts = ref<PostI[]>(sourceData.posts)
const users = ref<UserI[]>(sourceData.users)

const postById = (postId: string) => {
    return posts.value.find(post => post.id === postId)
}
const userById = (userId: undefined | string) => {
    return users.value.find(user => user.id === userId)
}
</script>

<template>
    <div class="container mx-auto sm:px-6 lg:px-8">
        <!-- Content goes here -->
    </div>
    <h1>Threads</h1>
    <div v-for="thread in threads" :key="thread.id">
        <h2>{{ thread.title }}</h2>
        <div v-for="postId in thread.posts" :key="postId">
            <p>{{ userById(postById(postId)?.userId)?.name }}</p>
            <p>{{ postById(postId)?.text }}</p>
        </div>
    </div>
</template>