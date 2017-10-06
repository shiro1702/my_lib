<template lang="pug">
div.container
    h1(v-if='h1').title {{h1}}

    slot

</template>

<script>
    export default {
		props: ['h1'],
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

.container {
	max-width: 1020px;
    margin: 0 auto;

}


</style>
