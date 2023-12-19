<!-- TreeNode.vue -->
<template>
    <div>
      <div @click="toggle" class="node" style="cursor: pointer;">
        {{ node.name }}
        <span v-if="node.children && node.children.length" style="cursor: pointer;">
          <!-- {{ node.isOpen ? '[-]' : '[+]' }} -->
        </span>
      </div>
      <div v-if="node.isOpen" style="margin-left: 20px;">
        <TreeNode v-for="child in node.children" :key="child.name" :node="child" @toggle="toggleChild" />
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      node: Object,
    },
    methods: {
      toggle() {
        this.$emit('toggle', this.node);
      },
      toggleChild(childNode) {
        this.$emit('toggle', childNode);
      },
    },
    components: {
    //   TreeNode,
    },
  };
  </script>

<style scoped>
    .node{
        display: block;
        background-color: bisque;
        width: 200px;
        /* height: 100px; */
        font-size: 30px;
        align-items: center;
        padding: 10px;
        margin-bottom: 30px;
    }
</style>
  