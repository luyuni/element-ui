<template>
  <div>
    <h3>Child</h3>
    <h5>{{msg}}</h5>
    <h6>{{childMsg}}</h6>
    <button @click="passMsg">走你！</button>
  </div>
</template>

<script>
import bus from '../util/bus'
export default {
  props: {
    msg: {
      type: String,
      default: ''
    },
  },
  data () {
    return {
      childMsg: 'child msg'
    }
  },
  methods: {
    passMsg () {
      this.$emit('showMsg', 'i am from Child')
    }
  },
  mounted () {
    console.log('attrs',this.$attrs)
    bus.$on('msg', (val) => {
      this.childMsg = val
    });
  },
}
</script>

<style scoped>
</style>