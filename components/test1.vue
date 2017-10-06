<template lang="pug">
h1.title привет {{ msg }} !!!
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

<style>
.title{
    color:red;
}

</style>
