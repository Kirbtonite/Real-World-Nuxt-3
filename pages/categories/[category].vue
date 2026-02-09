<script setup lang="ts">
import type { CategoryDetails } from '~/data/categories'
import { getCategoryDetailsUrl } from '~/data/categories'
const categorySlug = useParam('category')
const { data: category } = await useFetch<CategoryDetails>(
  getCategoryDetailsUrl(categorySlug)
)
</script>
<template>
    <main>
        <template v-if="category">
            <h1>
                {{ category.name }}
            </h1>
            <PostCard
                v-for="post in category.posts"
                :key="post.id"
                :post="post"
            />
        </template>
    </main>
</template>
