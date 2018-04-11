<template>
    <div :title="hello">
        <p>{{hello}}</p>
        <button @click="emitMyEvent">emit</button>
    </div>
</template>

<script>
export default {
  data () {
    return {
      hello: 'i am componenta'
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
