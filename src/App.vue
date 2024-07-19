<template>
  <div>
    <el-button @click="open">打开</el-button>
<el-button @click="open2">打</el-button>
  </div>
  <ChildComponent v-model:visible="flag" :text="inputTest"></ChildComponent>
</template>
<script>

import {ref, watch} from 'vue'
import ChildComponent from "@/components/ChildComponent.vue";

export default {
  name: 'App',
  components: {
    ChildComponent
  },
  data() {
    return {
      dialogVisible: false,
      inputTest: 'test'
    };
  },
  methods: {
    handleClose(done) {
      this.$confirm('确认关闭？')
          // eslint-disable-next-line no-unused-vars
          .then(_ => {
            done();
          })
          // eslint-disable-next-line no-unused-vars
          .catch(_ => {
          });
    }
  }, setup() {
    const flag = ref(false)

    const open = () => {
      flag.value = true
      this.inputTest = "fuck you"
    }
    const open2 = () => {
      flag.value = true
      this.inputTest = "fuck you again"
    }

    watch(() => flag.value, (val) => {
      console.log("监听flag值得变化:", val)
    })

    return {
      flag,
      open,
      open2
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
