<script setup>
import { Link } from '@inertiajs/vue3';

const props = defineProps({
    links: Array,

})
</script>

<template>
    <div>
        <div class="flex flex-wrap -mb-1 space-x-1">
            <template v-for="(link, p) in links" :key="p">
                <div v-if="link.url === null" class="mb-1 px-4 py-3 text-sm leading-4 text-gray-400 border rounded"
                    v-html="link.label"></div>
                <Link v-else
                    class="mb-1 px-4 py-3 text-sm leading-4 border rounded-lg hover:bg-gray-500 hover:text-white"
                    :class="{ 'bg-black text-white hover:bg-gray-400': link.active }" :href="link.url" v-html="link.label"></Link>
            </template>
        </div>
    </div>
</template>
