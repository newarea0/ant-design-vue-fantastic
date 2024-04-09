// App.vue
<script lang="ts">
import { S2Options } from '@antv/s2'
import type { S2DataConfig } from '@antv/s2'
import { SheetComponent } from '@antv/s2-vue'
import { defineComponent, onMounted, reactive, shallowRef } from 'vue'
import '@antv/s2-vue/dist/style.min.css'
import { rawOptions, s2DataConfig } from './data'

export default defineComponent({

  components: {
    SheetComponent,
  },
  setup() {
    const s2 = shallowRef()
    // dataCfg 数据字段较多，建议使用 shallow, 如果有数据更改直接替换整个对象
    const dataCfg = shallowRef(s2DataConfig)
    const options: S2Options = reactive(rawOptions)

    onMounted(() => {
      console.log('s2 instance:', s2.value?.instance)
    })
    return {
      s2,
      dataCfg,
      options,
    }
  },
})
</script>

<template>
  <SheetComponent ref="s2" :data-cfg="dataCfg" :options="options" />
</template>
