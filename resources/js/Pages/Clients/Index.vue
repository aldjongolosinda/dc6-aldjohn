<script setup>
    import SideLayout from '@/Layouts/SideLayout.vue'
    import ClientCard from '@/Components/ClientCard.vue';
    import Pagination from '@/Components/Pagination.vue';

const props = defineProps({
    clients: Object
})
</script>

<template>

<SideLayout>
    <div class="p-8" style="padding: 12px; background-color: #ffffff">
        <h1 class="text-4xl text- my-6">Clients List</h1>
    </div>

    <div class="py-8">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="flex flex-wrap w-full">
                    <ClientCard v-for="client in props.clients.data" :key="client.id" :client="client" />
                </div>

                <div class="flex justify-center items-center mt-10">
                    <Pagination
                        :links="clients.links"
                    />
                </div>
            </div>
        </div>
</SideLayout>

</template>
