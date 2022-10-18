<template>

        <h1 class="text-lg mb-2">Пост</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sky-500 text-sm mb-8">Назад</Link>
        </div>
        <div v-if="post">
            <div class="mt-8 pt-8 border-t border-gray-300">
                <div>id: {{post.id}}</div>
                <div>заголовок: {{post.title}}</div>
                <div>содержание: {{post.content}}</div>
                <div class="text-sm text-right">{{post.date}}</div>
            </div>
        </div>
</template>

<script>
import {Link} from '@inertiajs/inertia-vue3'
import MainLayout from "@/Layouts/MainLayout.vue";
export default {
    name: "Index",
    layout: MainLayout,
    props: [
        'post'
    ],
    components: {
        Link
    }
}
</script>

<style scoped>

</style>
