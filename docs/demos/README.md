## 介绍

这边是关于属性的使用示例，初步使用过程中 VuePress 的页面结构限制了示例的演示。初步的解决方案是将所有的组件包裹在一个固定的 Layout 中，然后利用插槽解决，当然 VuePress 给予了我们自己构建页面结构的能力，不过该项的处理需要延期处理。

## 使用

每次新创建一个展示组件时，都需要在外围包裹布局组件，示例：

```vue
<template>
  <Layout-Layout align-center justify-center>
    你好，欢迎来到 CSS 搞事技巧。
  </Layout-Layout>
</template>
```

目前对于布局提供了两个属性：`align-center` 和 `justify-center`，便于居中方案。