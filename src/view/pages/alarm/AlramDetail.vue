<!--
 * @Author: chaoxiaoshu-mx leukotrichia@163.com
 * @Date: 2023-02-07 11:04:52
 * @LastEditors: chaoxiaoshu-mx leukotrichia@163.com
 * @LastEditTime: 2023-03-13 15:02:56
 * @FilePath: \ThingsPanel-Backend-Vue\src\view\pages\alarm\AlramDetail.vue
 * @Description: 告警详情
-->

<template>
  <el-dialog :title="$t('ALARM.ALARAM_DETAIL')" class="el-dark-dialog" :visible.sync="dialogVisible"
    width="600px"  top="10vh">
    <el-form class="el-dark-input" label-position="left" label-width="85px">
      <el-form-item :label="$t('ALARM.ALARAM_CONTENT')">
        <el-input type="textarea" readonly  :rows="3" v-model="formData.warning_content"></el-input>
      </el-form-item>

      <div class="text-right">
        <el-button size="medium" type="cancel" @click="handleCancel">{{ $t('COMMON.CLOSE') }}</el-button>
      </div>
    </el-form>
  </el-dialog>
</template>
  
<script>
export default {
  name: "AlarmDetail",
  props: {
    data: {
      type: [Object, Array],
      default: ""
    },
    visible: {
      type: [Boolean],
      default: false
    }
  },
  data() {
    return {
      formData: {}
    }
  },
  computed: {
    dialogVisible: {
      get() {
        return this.visible;
      },
      set(val) {
        this.$emit("update:visible", val);
      }
    }
  },
  watch: {
    visible: {
      handler(newValue) {
        if (newValue) {
          this.initFormData();
        }
      }
    }
  },
  methods: {
    initFormData() {
      this.formData = JSON.parse(JSON.stringify(this.data));
    },
    handleCancel() {
      this.dialogVisible = false;
    }
  }
}
</script>
  
<style scoped></style>