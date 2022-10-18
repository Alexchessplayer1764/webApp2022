<template>
        <h1 class="text-lg mb-8">Посты</h1>
        <div class="mb-8">
            <Link :href="route('post.create')" class="hover:bg-white hover:text-sky-500 block p-2 w-36 border border-sky-500 bg-sky-500 rounded-full text-center text-white">Добавить пост</Link>
        </div>
        <div v-if="posts">
            <div class="mt-8 pt-8 border-t border-gray-300" v-for="post in posts">
                <div>id: {{post.id}}</div>
                <div>заголовок: {{post.title}}</div>
                <div>содержание: {{post.content}}</div>
                <div class="text-sm text-right">{{post.date}}</div>
                <div class="text-sm text-right">
                    <Link class="text-sky-500" :href="route('post.show',post.id)">Показать</Link>
                </div>
                <div class="text-sm text-right">
                    <Link class="text-sky-500" :href="route('post.edit',post.id)">Редактировать</Link>
                </div>
                <div class="text-sm text-right">
                    <p @click="deletePost(post.id)"  class="cursor-pointer text-red-500">Удалить</p>
                </div>
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
        'posts'
    ],
    components: {
        Link
    },
    methods: {
        deletePost(id){
            this.$inertia.delete(`/posts/${id}`)
        }
    }
}
</script>

<style scoped>

</style>
