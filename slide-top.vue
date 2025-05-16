<template>
  <div v-if="$page > 1" fixed inset-x-2 bottom-1 text-10px op-40 flex items-center>
    <div>
      JsShaker: 一个 JavaScript 代码体积优化器
    </div>
    <div flex-grow />
    <div class="font-[Consolas]">
      https://github.com/kermanx/tree-shaker
    </div>
    <div text-sm op-40 mb-1>
      <!-- <span v-if="$page % 2 === 0">
        JsShaker: 一个 JavaScript 代码体积优化器
      </span>
      <span v-else class="font-[Consolas]">
        https://github.com/kermanx/tree-shaker
      </span> -->
    </div>
  </div>
</template>
