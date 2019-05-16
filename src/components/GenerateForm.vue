<!--
 * @TODO: 
 * @Author: haoming
 * @Date: 2019-05-16 11:19:16
 * @LastEditors: haoming
 * @LastEditTime: 2019-05-16 16:18:45
 -->

<script>
import { Form, Input, Select } from 'element-ui'

let mapObj = new Map()
mapObj.set('form', Form)
mapObj.set('input', Input)
mapObj.set('select', Select)

let componentList = ['select']

export default {
  functional: true,
  props: {
    items: {
      type: Object,
      required: true
    }
  },
  render: function (createElement, context) {
    function appropriateListComponent () {
      var items = context.props.items
      // 匹配组件
      if (mapObj.get(items.type)) {
        return mapObj.get(items.type)
      }
      return <span></span>
    }
    return createElement(
      appropriateListComponent(),
      context.data,
      context.children
    )
  }
}
</script>

<style>
</style>