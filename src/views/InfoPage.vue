<template>
  <div>
    <div class="infoBar">
        <div class="rawBar"></div>
        <div class="wordCont">
            <span class="title">紡織原料</span>
            <span class="factoryName">US Fabric Supplier</span>
        </div>
    </div>
    <div class="wrap">
      <div class="demo-collapse">
        <el-collapse accordion>
          <el-collapse-item name="1">
            <template #title><span class="info">商品資訊 product attachments</span></template>
              <div class="infoBody">
                <div id="body">
                  <span id="id">#Lot </span>
                  <el-button size="large" @click="showInvoice"><span class="button">發票內容 invoice</span></el-button>
                  <el-button size="large"><span class="button">付費重量 payload</span></el-button>
                </div>
              </div>
          </el-collapse-item>
        </el-collapse>
      </div>
      <div class="map">
        <img src="@/assets/googlemap.png" id="mapImg">
        <span id="location"><el-icon id="icon"><location/></el-icon>美國 U.S Frabics Inc</span>
      </div>
    </div>
    <div class="detailed">
      <div id="first">
        <span class="title2">產品製造資訊 production</span>
        <div id="inside">
          <span id="date">2011/02/13  <span>am 09：15</span></span>
          <span>實際產品名稱 product title</span>
          <span>數量 quantity</span>
          <span>批發號 #LOT</span>
        </div>
      </div>
      <div id="sec">
        <span class="title2">運送資訊 shipping</span>
        <div id="inside">
          <span id="date">2011/02/13  <span>am 09：15</span></span>
          <span>出貨地 from</span>
          <span>送至 to</span>
          <span>接收地 receiver</span>
          <span>批發號 #LOT</span>
          </div>
      </div>
    </div>
    <div class="background" v-show="invioceShowed">
      <el-card class="box-card">
        <template #header>
          <div class="card-header">
            <span>發票資訊 Invoice information</span>
            <el-button class="button" @click="showInvoice"><el-icon><close/></el-icon></el-button>
          </div>
        </template>
        <div class="textItem">
          <div class="left">
            <span id="leftText">LastUpdated: 2019/08/05</span>
            <img src="@/assets/invoice.png" class="invoiceImg">
          </div>
          <div class="right">
            <span class="tit">發行日期 Issue date</span><span><el-icon class="icon"><Calendar /></el-icon>2019/08/05</span>
            <span class="tit">類型 type</span><span><el-icon class="icon"><Van /></el-icon>原料運送</span>
            <span class="tit">hash code</span><span><el-icon class="icon"><Connection /></el-icon>4x2lu6KpZUthHdLw$Adj</span>
          </div>
          
        </div>
      </el-card>
    </div>
    
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  setup(){
    const invioceShowed = ref(false);
    const showInvoice = () =>{
      invioceShowed.value = !invioceShowed.value;
    }
    return{
      showInvoice,
      invioceShowed,
    }
  }

}
</script>

<style scoped>
    .infoBar{
        display: flex;
        margin: 40px;
    }
    .rawBar{
        height: 90px;
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
        font-size: 28px;
        font-style: normal;
        font-weight: 500;
        line-height: normal;
    }

    .demo-collapse{
      width: 77%;
      padding: 0 40px ;
      
    }
    .info{
      font-size: 25px;
    }

    .infoBody{
      /* height: 60px; */
      align-content: center;
      margin: auto 0;
      /* background-color: #F4F4F4; */
      text-align: center;
      border-top: 1px solid;
    }

    #id{
      font-size: 22px;
    }
    #body{
      position: relative;
      top: 20px;
      margin: 0 auto;
      display: flex;
      gap: 50px;
      height: 60px;
      /* border-top: 1px solid; */
      /* text-align: center; */

    }
    .button{
      font-size: 22px;
      padding: 10px;
    }

    #mapImg{
      width: 80%;
      height: auto;
    }
    .wrap{
      display: flex;
      gap: 5px;
    }

    #location{
      display: block;
      padding: 20px;
      font-size: 25px;
      /* align-items: center; */
    }
    #icon{
      font-size: 25px;
      padding-right: 10px;
      color: #D13F3F;
    }
    .title2{
      display: block;
      font-size: 22px;
      /* position: absolute; */
      /* top: 350px; */
      margin-left:40px;
      padding: 10px 20px;
      background: #FFEBD8;
      border-radius: 10px;
      margin-bottom: 10px;

      
    }
    #inside{
      display: flex;
      gap: 30px;
      text-decoration: underline;
      font-size: 22px;
      position: absolute;
      /* top: 400px; */
      margin-left:40px;
      width: 900px;
    }
    #date{
      display: block;
    }

    .title3{
      display: block;
      font-size: 22px;
      /* position: absolute; */
      /* top: 350px; */
      margin-left:40px;
    }

    #first{
      /* gap: 40px; */
      position: absolute;
      top: 350px;
      /* width: 300px; */
    }
    #sec{
      position: absolute;
      top: 500px;
    }
    .box-card{
      width: 90vw;
      height: 95vh;
      position: absolute;
      left: 5vw;
      top: 2.5vh;
      font-size: 22px;
    }

    .background{
      position: absolute;
      top: 0;
      left: 0;
      background: rgba(0, 0, 0, 0.6);
      z-index: 10;
      width: 100vw;
      height: 100vh;
    }

    .card-header{
      display: flex;
      justify-content: space-between;
      font-size: 36px;
    }

    #leftText{
      display: block;
      /* font-size: 30px; */
    }

    .left{
      position: absolute;
      left: 10%;
      display: block;
      /* padding: 0 30px; */
      
    }
    .invoiceImg{
      height: 100%;
      padding: 30px;
    }
    .textItem{
      position: relative;
      padding: 30px;
      font-size: 30px;
      display: flex;
      gap: 100px;
    }
    .right{
      /* display: flex; */
      text-align: left;
      /* line-height: 2; */
      display: block;
      position: absolute;
      right: 30%;
      /* margin: 0 auto; */
    }
    .right>span{
      display: block;
      line-height: 2;
    }

    .tit{
      font-size: 40px;
      font-weight: 545;
      color: black;
      /* background: #FFD6B0; */
      border-radius: 10px;
    }

    .icon{
      line-height: 2;
      padding-right: 20px;
    }
    
</style>