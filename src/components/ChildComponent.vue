<template>
  <div class="hello">
    <el-dialog title="提示" v-model="dialogVisble" width="30%" :before-close="close">
      <span>这是一段信息</span>
      <template #footer>
        <span class="dialog-footer">
          <el-button @click="close">取 消</el-button>
          <el-button type="primary" @click="confirm">确 定</el-button>
        </span>
      </template>
    </el-dialog>
  </div>
</template>

<script>
  import { ref, watch } from 'vue'

  export default {
    props: {
      visible: {
        type: Boolean,
        default: false
      }
    },

    setup(props, ctx) {

      const dialogVisble = ref(false)

      const close = () => {
        ctx.emit("update:visible", false);
      };

      const confirm = () => {
        console.log('你点击了确定按钮')
        ctx.emit("update:visible", false);
      }

      watch(() => props.visible, (val) => {
        console.log(props.visible, val);
        dialogVisble.value = val
      });

      return {
        dialogVisble,
        confirm,
        close
      }
    }
  }
</script>
