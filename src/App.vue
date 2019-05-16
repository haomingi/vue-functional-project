<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div>
      <p>
        If Element is successfully added to this project, you'll see an
        <code v-text="'<el-button>'"></code>
        below
      </p>
      <el-button @click="btnClick">el-button</el-button>
    </div>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <el-form>
      <div v-for="(item, index) in data" :key="index">
        <el-form-item v-for="items in item.list" :key="items.key">
          <GenerateForm
            :items="items"
            v-model="list[items.model]"
            v-bind="attrData[items.model]"
            v-on="functionData[items.model]"
          >
            <slot name="hm">
              <el-option
                v-for="item in attrData[items.model]['list']"
                :key="item.value"
                :label="item.label"
                :value="item.value"
              ></el-option>
            </slot>
          </GenerateForm>
        </el-form-item>
      </div>
    </el-form>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import GenerateForm from './components/GenerateForm.vue'
import { Form, FormItem, Option } from 'element-ui'

const columns = [{
  "span": 6,
  "list": [{
    "key": "1556179867000_16494",
    "type": "input",
    "name": "运单号",
    "icon": "icon-input",
    "options": {
      "issys": 1,
      "width": "100%",
      "defaultValue": "",
      "required": false,
      "dataType": "string",
      "pattern": "",
      "placeholder": "",
      "remoteFunc": "func_1556179867000_16494"
    },
    "model": "waybillId",
    "rules": []
  }]
},
{
  "span": 6,
  "list": [{
    "key": "1556179867000_16495",
    "type": "select",
    "name": "客户名称",
    "icon": "icon-input",
    "options": {
      "issys": 0,
      "width": "100%",
      "defaultValue": "",
      "required": true,
      "dataType": "string",
      "pattern": "",
      "placeholder": "",
      "remoteFunc": "func_1556179867000_16494"
    },
    "model": "partnerId",
    "rules": [{
      "type": "string",
      "message": "请选择客户名称!"
    }]
  }]
},
{
  "span": 6,
  "list": [{
    "key": "1556179867000_16496",
    "type": "select",
    "name": "项目名称",
    "icon": "icon-input",
    "options": {
      "issys": 0,
      "width": "100%",
      "defaultValue": "",
      "required": true,
      "dataType": "string",
      "pattern": "",
      "placeholder": "",
      "remoteFunc": "func_1556179867000_16494"
    },
    "model": "projectId",
    "rules": [{
      "type": "string",
      "message": "请选择项目名称!"
    }]
  }]
},
{
  "span": 6,
  "list": [{
    "key": "1556179867000_16497",
    "type": "select",
    "name": "运输方式",
    "icon": "icon-input",
    "options": {
      "issys": 0,
      "width": "100%",
      "defaultValue": "",
      "required": false,
      "dataType": "string",
      "pattern": "",
      "placeholder": "",
      "remoteFunc": "func_1556179867000_16494"
    },
    "model": "transportType",
    "rules": []
  }]
}
]

export default {
  name: 'app',
  components: {
    HelloWorld,
    GenerateForm,
    ElForm: Form,
    ElFormItem: FormItem,
    ElOption: Option
  },
  data () {
    return {
      data: columns,
      list: {
        waybillId: 'ss',
        partnerId: '选项1',
        projectId: '选项3',
        transportType: '选项2'
      },
      functionData: {
        waybillId: {
          change: this.inputClick,
          blur: this.inputBlur
        },
        partnerId: {
          change: this.selectChange
        }
      },
      attrData: {
        waybillId: {
          placeholder: "请选择活动区域"
        },
        partnerId: {
          list: [{
            value: '选项1',
            label: '黄金糕'
          }, {
            value: '选项2',
            label: '双皮奶'
          }, {
            value: '选项3',
            label: '蚵仔煎'
          }, {
            value: '选项4',
            label: '龙须面'
          }, {
            value: '选项5',
            label: '北京烤鸭'
          }]
        },
        projectId: {
          list: [{
            value: '选项1',
            label: '黄金糕'
          }, {
            value: '选项2',
            label: '双皮奶'
          }, {
            value: '选项3',
            label: '蚵仔煎'
          }]
        },
        transportType: {
          list: [{
            value: '选项1',
            label: '黄金糕'
          }, {
            value: '选项2',
            label: '双皮奶'
          }, {
            value: '选项3',
            label: '蚵仔煎'
          }]
        }
      }
    }
  },
  methods: {
    inputClick (cc) {
      console.log(cc)
    },
    inputBlur () {
      console.log('wwww')
    },
    btnClick () {
      console.log(this.list.waybillId)
    },
    selectChange (val) {
      console.log(val)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
