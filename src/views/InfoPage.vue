<template>
  <div>
    <div class="infoBar">
        <div class="rawBar"></div>
        <div class="wordCont">
            <span class="title">紡織原料</span>
            <span class="factoryName">US Fabric Supplier</span>
        </div>
    </div>
    <div class="demo-collapse">
    <el-collapse accordion>
      <el-collapse-item name="1">
        <template #title>
          Consistency<el-icon class="header-icon">
            <info-filled />
          </el-icon>
        </template>
        <div>
          Consistent with real life: in line with the process and logic of real
          life, and comply with languages and habits that the users are used to;
        </div>
        <div>
          Consistent within interface: all elements should be consistent, such
          as: design style, icons and texts, position of elements, etc.
        </div>
      </el-collapse-item>
    </el-collapse>
    </div>
                            
    
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
    .infoBar{
        display: flex;
        margin: 40px;
    }
    .rawBar{
        height: 80px;
        width: 10px;
        background-color: #FFD6B0;
        border-radius: 30px;
    }

    .wordCont{
        display: grid;
        row-gap: 14px;
        /* justify-content: left; */
        text-align: left;
        padding-left: 20px;
    }

    .title{
        color: #000;
        /* font-family: Inter; */
        font-size: 22px;
        font-style: normal;
        font-weight: 500;
        line-height: normal;
    }

</style>