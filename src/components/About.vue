<template>
    <div class="flex align-center justify-center">
        <div class="flex align-center w-64 flex-wrap flex-col gap-4 mt-20">
            <h1 class="text-2xl">
                About {{ name }}
            </h1>
            <router-link to="/" class="bg-gray-600 text-white py-2 px-6 rounded text-center">Back</router-link>
        </div>
    </div>
</template>

<script setup>   

import { computed, ref } from 'vue'
import { useStore} from 'vuex'

const store = useStore()

const name = computed(() => {
    return store.state.user.name
})

</script>
