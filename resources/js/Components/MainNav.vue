<script setup>
    import { Link } from '@inertiajs/vue3';
</script>

<template>

    <div id="sidebar" class="p-6 duration-500 bg-primary" :class="width" style="position: relative;">
        <div class="main-nav">
            <Link href="/dashboard">
                <i class="fa fa-home"></i> Dashboard</Link>
            <Link href="/clients">
                <i class="fa fa-user" aria-hidden="true"></i> Clients List</Link>
        </div>
    </div>

</template>


