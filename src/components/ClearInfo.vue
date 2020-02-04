<template>
    <ion-button color="light" expand="block" v-if="info" @click="$emit('clearInfoHandler')">
        Clear
    </ion-button>
</template>

<script>
export default {
    name: 'ClearInfo',
    props: {
        info: {
            type: Object
        }
    }
}
</script>