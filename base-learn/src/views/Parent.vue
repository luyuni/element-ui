<template>
  <div>
    <h1>Parent</h1>
    <h3>{{msg}}</h3>
    <h5>vuex <span style="color: red">{{count}}</span></h5>
    <h5>getters <span style="color: red">{{doubleCount}}</span></h5>
    <button @click="add">增加</button>
    <m-child msg="from Parent msg" @showMsg="showMsg" ref="child" v-bind="$attrs"></m-child>
  </div>
</template>

<script>
import MChild from './Child'
import { mapState, mapGetters } from 'vuex'
export default {
  // computed: {
  //   count() {
  //     return this.$store.state.count
  //   }
  // },
  computed: {
    ...mapState({
      count: state => state.text.count
    }),
    ...mapGetters([
      'doubleCount'
    ])
  },
  data () {
    return {
      msg: ''
    }
  },
  components: {
    MChild,
  },
  methods: {
    showMsg (val) {
      this.msg = val
    },
    add() {
      // this.$store.commit('add')
      this.$store.dispatch('delayAdd')
    }
  },
  mounted () {
    console.log(this.$children[0]);
    console.log('ref', this.$refs.child)
  },
}
</script>

<style scoped>
</style>