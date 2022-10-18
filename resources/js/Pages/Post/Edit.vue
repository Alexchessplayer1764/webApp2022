<template>
        <h1 class="text-lg mb-4">Редактирование</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sky-500 text-sm mb-8">Назад</Link>
        </div>

        <form @submit.prevent="update">
            <div class="mb-4">
                <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="заголовок">
            </div>
            <div class="mb-4">
                <textarea v-model="content" class="w-full rounded-full border-gray-300" placeholder="содержание"></textarea>
            </div>
            <div>
                <button class="ml-auto hover:text-sky-500 block p-2 w-32 border border-sky-500 bg-sky-500 rounded-full text-center text-white" type="submit">Обновить</button>
            </div>
        </form>
</template>

<script>
import {Link} from '@inertiajs/inertia-vue3'
import MainLayout from "@/Layouts/MainLayout.vue";
export default {
    name: "Index",
    components: {
        Link
    },

    layout: MainLayout,
    props: [
        'post'
    ],

    data(){
        return{
            id: this.post.id,
            title: this.post.title,
            content: this.post.content,
        }
    },
    methods: {
        update(){
           this.$inertia.patch(`/posts/${this.id}`, {title: this.title, content: this.content})
        }
    }
}
</script>

<style scoped>

</style>
