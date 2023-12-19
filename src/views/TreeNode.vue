<!-- TreeNode.vue -->
<template>
    <div>
      
      <div @click="toggle"  style="cursor: pointer;">
        <!-- <span>{{ title }}</span> -->
        <div :class="['node', `level-${node.level}`]">{{ node.name }}</div>
        <span v-if="node.children && node.children.length" style="cursor: pointer;">
          <!-- {{ node.isOpen ? '[-]' : '[+]' }} -->
        </span>
      </div>
      <div v-if="node.isOpen" style="margin-left: 400px;">
        <TreeNode v-for="child in node.children" :key="child.name" :node="child" @toggle="toggleChild" />
      </div>
    </div>
  </template>
  
  <script>
  export default {
    components: {
    //   TreeNode,
    },
    props: {
      node: Object,
      level: Number,
    },
    data(){
      return{
        title:"",
      };
    },
    
    methods: {
      name(){
        if(this.level === '0'){
          this.title = "產品";
        }
        else if(this.level === '1'){
          this.title = "銷售商 seller";
        }
        else if(this.level === '2'){
          this.title = "加工處理 processor";
        }
        else{
          this.title = "供應商 supplier";
        }
      },
      toggle() {
        this.$emit('toggle', this.node);
      },
      toggleChild(childNode) {
        this.$emit('toggle', childNode);
      },
      
    },
    created() {
        this.name(); // 在組件創建時調用 name 函數
    },
    
  };
  </script>

<style scoped>
    .node{
        display: block;
        /* background-color: bisque; */
        width: 200px;
        /* height: 100px; */
        font-size: 30px;
        align-items: center;
        padding: 5px;
        margin-bottom: 10px;
        border-radius: 20px;
        margin-left: 30px;
    }
    .level-0{
      background-color: #FFF2E5;
      position:relative;
      top:300px

    }
    .level-1{
      background-color: #FFEBD8;
      /* margin-bottom: 500px; */
    }

    .level-2{
      background-color: #FFDCBC;
    }

    .level-3{
      background-color: #FFC187;
    }
</style>
  