<script setup>
    import MainNav from '@/Components/MainNav.vue'
    import { ref, provide } from 'vue';

    let width = ref('w-[250px]')
    let hide = ref(false)

    function toggleWidth() {
        if(width.value == 'w-[250px]') {
            width.value = 'w-[100px]'
            hide.value = true
        }else {
            width.value = ['w-[250px]']
            hide.value = false
        }
    }

    const accent = ref('')

    function setColorToBlue() {
        accent.value = 'Blue';
    }
    function setColorToRed() {
        accent.value = 'Red';
    }
    function setColorToGreen() {
        accent.value = 'Green';
    }
    function setColorToGray() {
        accent.value = 'Gray';
    }

    provide('accent', accent)
</script>

<template>
    <div class="flex min-h-screen">
        <div id="sidebar"
        :class="{
                'bg-gray-900' : accent == 'Gray',
                'bg-blue-600' : accent == 'Blue',
                'bg-red-600' : accent == 'Red',
                'bg-green-600' : accent == 'Green',
                width
            }"
        class="p-5 duration-700" style="position: relative;">
            <button class="text-xl text-gray-900" @click="toggleWidth" style="position: absolute; right: 10px; top:10px">
                <i class="fa-solid fa-bars"></i>
            </button>
            <div id="branding" :hidden="hide">
                <img src="https://scontent.fmnl3-4.fna.fbcdn.net/v/t39.30808-6/336257333_555031126610315_2677896213364470090_n.jpg?_nc_cat=104&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeHo0dAZz8LYmw9K8J3x6l7f2QcEp38DJ0bZBwSnfwMnRonWjBv4dwF3sP6q28DoUQDejNjaJ4ih5OFNpE4C5mSx&_nc_ohc=JG9guov2zEgAX89Osjx&_nc_zt=23&_nc_ht=scontent.fmnl3-4.fna&oh=00_AfA8d7KbgDvsbENVRjD-bbBGqHKEtSQC7Sq-vVL2dvtxsA&oe=6518C4D6" alt="MISFITS"
                    class="w-[170px] h-[170px] mx-auto rounded-full object-cover">
                <h1 class="text-3xl text-center text-gray-200 my-6"></h1>
                <h1 class="my-6 text-3xl text-center text-gray-400">{{ $page.props.auth.user.name }}</h1>

            </div>
            <hr class="border-gray-900">

            <MainNav :hidden="hide"></MainNav>

            <div class="mt-10">

                    <div id="sidebar" class="p-6 duration-700 bg-primary" :class="width" style="position: relative;">
                        <div class="dropdown">
                            <button class="dropbtn"></button>
                            <div class="dropdown-content">
                                <button
                                @click="setColorToBlue()"
                                type="button"
                                class="rounded-l-md px-4 py-1.5 bg-blue-600 text-sm text-white w-[70px]">Blue</button>
                                <button
                                @click="setColorToRed()"
                                type="button"
                                class="px-4 py-1.5 bg-red-600 text-sm text-white w-[70px]">Red</button>
                                <button
                                @click="setColorToGreen()"
                                type="button"
                                class="px-4 py-1.5 bg-green-600 text-sm text-white w-[70px]">Green</button>
                                <button
                                @click="setColorToGray()"
                                type="button"
                                class="rounded-r-md px-4 py-1.5 bg-gray-900 text-sm text-white w-[70px]">Gray</button>
                            </div>
                        </div>

                    </div>
            </div>

        </div>
        <div id="container" class="flex-2">
            <slot />
        </div>

    </div>

</template>
