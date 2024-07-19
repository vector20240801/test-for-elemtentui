<template>
  <div>
    <el-button @click="open">打开</el-button>
    <ChildComponent v-model:visible="flag"></ChildComponent>
  </div>
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
      dialogVisible: false
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
    }

    watch(() => flag.value, (val) => {
      console.log("监听flag值得变化:", val)
    })

    return {
      flag,
      open
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
