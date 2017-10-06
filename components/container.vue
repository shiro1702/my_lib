<template lang="pug">
div.container
    h1.title заголовок контейнера {{ msg }} !!!
    slot

</template>

<script>
    export default {
        data () {
            return {
                msg : "shiro"
            }
        },
        components: {
        }
    }
</script>

<style lang="scss">
.container:hover{
    box-shadow:0 0 1px red;
}

</style>
