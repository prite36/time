<template lang="html">
  <div class="">
    {{h1}}  {{h2}} :   {{m1}}{{m2}}  :  {{s1}} {{s2}} : {{ms}} <br>
    <button type="button" name="button" @click="startTime()" v-show="start">Start</button>
    <button type="button" name="button" @click="stopTime()" v-show="!start">Stop</button>
    <button type="button" name="button" @click="reset()">Reset</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      h1: 0,
      h2: 0,
      m1: 0,
      m2: 0,
      s1: 0,
      s2: 0,
      ms: 0,
      time: '',
      start: true
    }
  },
  computed: {},
  mounted () {},
  methods: {
    startTime: function () {
      var vm = this
      this.ms += 1
      this.time = setInterval(function () {
        vm.ms += 1
        if (vm.ms === 100) {
          vm.s2 += 1
          vm.ms = 0
        }
        if (vm.s2 === 10) {
          vm.s1 += 1
          vm.s2 = 0
        }
        if (vm.s1 === 6) {
          vm.m2 += 1
          vm.s1 = 0
        }
        if (vm.m2 === 10) {
          vm.h2 += 1
          vm.m2 = 0
        }
        if (vm.m1 === 6) {
          vm.h2 += 1
          vm.m1 = 0
        }
        if (vm.h2 === 10) {
          vm.h1 += 1
          vm.h2 = 0
        }
      }, 10)
      this.start = false
    },
    stopTime: function () {
      this.start = true
      clearInterval(this.time)
    },
    reset () {
      var vm = this
      vm.ms = vm.s1 = vm.m2 = vm.m1 = vm.h2 = vm.h1 = 0
    }
  },
  components: {}
}
</script>

<style lang="css">
</style>
