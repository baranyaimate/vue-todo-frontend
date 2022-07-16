<template>
<div>
    <h1>Home</h1>
    <p>This is the Home component.</p>
    <p>Name in store: {{ name }}</p>

    <input v-model="newName" type="text" class="border-gray-900"/>
    <button @click="saveName" >Submit</button>
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
