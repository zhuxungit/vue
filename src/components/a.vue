<template>
    <div>
        {{ hello }}
        {{ myValue }}
        <button @click="emitMyEvent">emit</button>
        <slot name="header">no header</slot>

        <slot name="footer">no footer</slot>
    </div>
</template>

<script type="text/ecmascript-6">
    export default {
        props:{
            'myValue':[String]
        },
        data () {
            return {
                hello: 'i am component a'
            }
        },
        methods: {
            emitMyEvent () {
                this.$emit('my-event',this.hello)
            }
        }
    }
</script>

<style>
</style>