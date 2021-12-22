<!--
 * @Author: Tango
 * @Date: 2021-12-21 16:03:43
 * @LastEditTime: 2021-12-21 17:35:27
 * @LastEditors: Tango
 * @Description: 
 * @FilePath: \admin-low-code\src\views\admin\index.vue
 * 可以输入预定的版权声明、个性签名、空行等
-->
<template>
  <div>
    <div class="left-component">
      <div>
        <h1>可拖动组件库</h1>
        <div class="component-list">
          <draggable
            :list="myArray"
            group="people"
            ghost-class="ghost"
            @start="start"
            @end="end"
            :move="checkMove"
            item-key="id"
          >
            <template #item="{ element }">
              <div>{{ element.name }}</div>
            </template>
          </draggable>
        </div>
      </div>
    </div>
    <div class="center-component"></div>
    <div class="right-component"></div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import draggable from 'vuedraggable'
export default defineComponent({
  name: 'admin',
  components: { draggable },
  setup() {
    let myArray = ref<any>([
      {
        id: '1',
        name: 'aaa'
      },
      {
        id: '2',
        name: 'bbb'
      }
    ])
    let drag: Boolean = false

    let start = () => {
      drag = true
    }
    let end = () => {
      drag = false
    }
    let checkMove = (e: any) => {
      console.log('Future index: ' + e.draggedContext.futureIndex)
    }
    return {
      myArray,
      drag,
      start,
      end,
      checkMove
    }
  }
})
</script>

<style lang="less" scoped></style>
