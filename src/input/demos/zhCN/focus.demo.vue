<markdown>
# 手动操作

清除、聚焦、失焦、选中、滚动。
</markdown>

<script lang="ts">
import type { InputInst } from 'naive-ui'
import { defineComponent, ref } from 'vue'

export default defineComponent({
  setup() {
    const inputInstRef = ref<InputInst | null>(null)
    return {
      inputInstRef,
      inputValue: ref('马儿乖，马儿好，马儿光跑不吃草。'.repeat(4)),
      handleClear() {
        inputInstRef.value?.clear()
      },
      handleFocus() {
        inputInstRef.value?.focus()
      },
      handleBlur() {
        inputInstRef.value?.blur()
      },
      handleSelect() {
        inputInstRef.value?.select()
      },
      handleScrollEnd() {
        inputInstRef.value?.scrollTo({
          behavior: 'smooth',
          left: 10000
        })
      }
    }
  }
})
</script>

<template>
  <n-space vertical>
    <n-space>
      <n-button @click="handleClear">
        Clear
      </n-button>
      <n-button @click="handleFocus">
        Focus
      </n-button>
      <n-button :focusable="false" @click="handleBlur">
        Blur
      </n-button>
      <n-button :focusable="false" @click="handleSelect">
        Select
      </n-button>
      <n-button :focusable="false" @click="handleScrollEnd">
        ScrollToEnd
      </n-button>
    </n-space>
    <n-input ref="inputInstRef" v-model:value="inputValue" />
  </n-space>
</template>
