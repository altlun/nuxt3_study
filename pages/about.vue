<script setup lang="ts">
import { Post } from '~/types';
const {data,pending,error} = await useFetch<Post>('https://dummyjson.com/posts/1')
</script>

<template>
    <div>
        <h1>About Page</h1>
        <NuxtLink to="/">Root</NuxtLink>
        <h1 v-if="pending">Loading</h1>
        <h1 v-else-if="error">Error</h1>
        <div v-else-if="data">
            <h1>Post Title: {{ data.title }}</h1>
            <h1>Post Body: {{ data.body }}</h1>
        </div>
    </div>
</template>