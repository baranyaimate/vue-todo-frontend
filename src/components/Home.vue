<template>
    <div class="flex align-center justify-center">
        <div class="flex align-center w-64 flex-wrap flex-col gap-4 mt-20">
            <h1 class="text-3xl">
                Home
            </h1>
            <p>This is the Home component.</p>
            <p>Name in store: {{ name }}</p>

            <input v-model="newName" type="text" class="bg-gray-100 border-2 border-gray-600 py-2 px-2 rounded" placeholder="Name"/>
            <button @click="saveName" class="bg-gray-600 text-white py-2 px-6 rounded text-center">Submit</button>
        </div>
    </div>
</template>

<script setup>   
import { computed, ref } from 'vue'
import { useStore} from 'vuex'
import { useRouter } from 'vue-router'

const store = useStore()
const router = useRouter()

const name = computed(() => {
    return store.state.user.name
})

const newName = ref('')

function saveName() {
    store.dispatch('saveName', newName.value)
    newName.value = ''
    router.push('/about')
}

</script>
