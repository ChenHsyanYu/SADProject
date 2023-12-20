<template>
    <div class="page">
        <div class="header">
            <!-- <span id="timeLine">Time Line</span> -->
            <span id="productTitle">衣服</span>
            <div style="margin-top: 20px">
                <el-radio-group v-model="radio2" fill="#FFD6B0" text-color="gray" @change="change">
                    <el-radio-button label="族譜圖" />
                    <el-radio-button label="產品資訊" />
                </el-radio-group>
            </div>
            <!-- <el-switch v-model="value1" @change="istrue" active-text="祖譜圖" inactive-text="產品資訊" class="switch"/> -->
        </div>
        <div class="timeSpan">
            <div id="span">
                <span>start</span>
                <div id="firstStep" class="span" @mouseenter="show('1')"  @mouseleave="unshow">   </div>
                <div id="secStep" class="span" @mouseenter="show('2')" @mouseleave="unshow">   </div>
                <div id="thirdStep" class="span" @mouseenter="show('3')" @mouseleave="unshow">   </div>
                <span>end</span>
            </div>
            
        </div>
        <div class="infoBody">
            <div class="info">
                <div class="text">
                    <span>Supplier 供應商</span>
                    <span class="factory">廠商數量：2</span>
                </div>
                <div class="barInfo">
                    <div class="body" style="cursor: pointer;" @click="toInfoPage">
                        <div class="rawBar"></div>
                        <div class="wordCont" >
                            <span class="title">紡織原料</span>
                            <span class="factoryName">factory A</span>
                        </div>
                            
                    </div>
                    <div class="body">
                        <div class="rawBar"></div>
                        <div class="wordCont">
                            <span class="title">絲料</span>
                            <span class="factoryName">factory B</span>
                        </div>
                    </div>
                    
                </div>
                
            </div>
            <div class="info">
                <div class="text" id="text2">
                    <span>Processsing 加工處理
                    </span>
                    <span class="factory">廠商數量：3</span>
                </div>
                <div class="barInfo" id="process">
                    <div class="body">
                        <div class="processBar"></div>
                        <div class="wordCont">
                            <span class="title">第一階段布料</span>
                            <span class="factoryName">factory C</span>
                        </div>
                            
                    </div>
                    <div class="body">
                        <div class="processBar"></div>
                        <div class="wordCont">
                            <span class="title">棉質布</span>
                            <span class="factoryName">factory D</span>
                        </div>
                    </div>
                    <div class="body">
                        <div class="rawBar"></div>
                        <div class="wordCont">
                            <span class="title">其他材質原料</span>
                            <span class="factoryName">factory E</span>
                        </div>
                    </div>
                    
                </div>
                 
            </div>
            <div class="info">
                <div class="text" id="text3">
                    <span>Seller 銷售商
                    </span>
                    <span class="factory">廠商數量：2</span>
                </div>
                <div class="barInfo" id="seller">
                    <div class="body">
                        <div class="sellerBar"></div>
                        <div class="wordCont">
                            <span class="title">品牌標示</span>
                            <span class="factoryName">seller A</span>
                        </div>
                            
                    </div>
                    <div class="body">
                        <div class="sellerBar"></div>
                        <div class="wordCont">
                            <span class="title">品牌印製</span>
                            <span class="factoryName">seller B</span>
                        </div>
                    </div>
                    
                </div>

            </div>

        </div>

        <div class="timeCard" id="first" v-show="showfirst">
            2011/02/13
        </div>
        <div class="timeCard" id="sec" v-show="showSec">
            2011/06/25
        </div>
        <div class="timeCard" id="end" v-show="showThird">
            2012/03/13
        </div>

    </div>
</template>

<script>
import { useRouter } from 'vue-router';
import { ref } from 'vue';
export default {
    setup(){
        const product_title = ref("紡織品一");
        const showfirst = ref(false);
        const showSec = ref(false);
        const showThird = ref(false);
        const router = useRouter();
        const value1 = ref(true);
        const radio2 = ref('產品資訊')

        const show = (index) =>{
            if(index === "1"){
                showfirst.value = true;
            }
            else if(index === "2"){
                showSec.value = true;
            }
            else{
                showThird.value = true;
            }
            
        }
        const unshow = () =>{
            showfirst.value = false;
            showSec.value = false;
            showThird.value = false;
        };

        const toInfoPage = ()=>{
            router.push('/infoPage');
        };

        const istrue = ()=>{
            console.log(value1);
        };

        const change = ()=>{
            if(radio2.value === "族譜圖"){
                router.push('/searchPage');
            }
        };

        return{
            product_title,
            showSec,
            showfirst,
            show,
            unshow,
            showThird,
            toInfoPage,
            value1,
            istrue,
            radio2,
            change,
        }
    }

}
</script>

<style scoped>
    .page{
        position: relative;
    }

    .header{
        height: 74px;
        width: 100%;
        position: absolute;
        top: 0;
        left: 0;
        align-items: center;
        display: flex;
    }
    #timeLine{
        display: block;
        width: 160px;
        height: 59px;
        /* flex-direction: column; */
        justify-content: center;
        flex-shrink: 0;
        color: #000;
        /* text-align: center; */
        /* font-family: Inter; */
        font-size: 22px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
    }
    #productTitle{
        color: #000;
        text-align: center;
        /* font-family: Inter; */
        font-size: 30px;
        font-style: normal;
        font-weight: 400;   
        line-height: normal;
        display: block;
        width: 447px;
        /* height: 41px; */
        /* flex-direction: column;  */
        justify-content: center;
        flex-shrink: 0;
        margin: 0 auto;
    }

    .timeSpan{
        width: 100vw;
        height: 36px;
        display: flex;
        position:absolute;
        top: 74px;
        padding: 8px 0;
        border-top: 1px solid gray;
        border-bottom: 1px solid gray;
        align-items: center;
        gap: 36px;
        /* text-align: center; */
        margin: 0 auto;
        justify-content: center;
    }

    .timeSpan .span{
        height: 20px;
        border-radius: 30px;
        background-color: #D9D9D9;
        display: block;
        cursor: pointer;
    }
    #span{
        display: flex;
        gap: 36px;
    }

    #firstStep{
        width: 250px;
    }
    #secStep{
        width: 800px;
    }
    #thirdStep{
        width: 250px;
    }
    .infoBody{
        display: flex;
        gap: 100px;
        position: absolute;
        top: 110px;
        padding: 50px 100px;
    }
    .info{
        width: 400px;
        height: 550px;
        box-shadow: 2px 2px 10px gray;
        text-align: center;
    }

    .text{
        display:grid;
        flex-direction: row;
        flex-wrap: wrap;
        background-color: #FFF3F3;
        width: 300px;
        height: 154px;
        color: #000;
        text-align: center;
        font-size: 30px;
        font-style: normal;
        font-weight: 500;
        line-height: normal;
        margin: 15px auto;
        padding: 28px;
        border-radius: 15px;
    }

    .factory{
        color: #000;
        text-align: center;
        font-size: 18px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
    }
    .barInfo{
        display: grid;
        flex-direction: row;
        gap: 20px;
        padding: 10px 25px;
        /* padding-top: 10px; */
        /* row-gap: 20px; */
    }
    .rawBar{
        height: 80px;
        width: 10px;
        background-color: #FFD6B0;
        border-radius: 30px;
    }

    .processBar{
        height: 80px;
        width: 10px;
        background-color: #C4B0FF;
        border-radius: 30px;
    }

    .body{
        display: flex;
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

    .factoryName{
        color: rgba(0, 0, 0, 0.69);
        /* font-family: Inter; */
        font-size: 18px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
    }

    #text2{
        background-color: #FFE9E9;
    }

    #process{
        padding-top: 10px;
        row-gap: 20px;
    }

    .sellerBar{
        height: 80px;
        width: 10px;
        background-color: #B0DEFF;
        border-radius: 30px;
    }

    .timeCard{
        position: absolute;
        top:30px;
        width: 92px;
        /* height: 32px; */
        background: #F4F4F4;
        box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
        /* padding: 10px 10px 0 10px; */
        padding: 10px 10px;
        align-items: center;
    }

    .timeCard::after{
        /* box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25); */
        content: '';
        display: block;
        width: 0;
        height: 0;
        border-top: 20px solid #F4F4F4;
        border-right: 20px solid transparent;
        border-left: 20px solid transparent;
        position: absolute;
        top: 30px;
        text-align: center;
        left: 32px;
        /* border: rgba(0, 0, 0, 0.25); */
    }

    #first{
        position: absolute;
        /* top: 30px; */
        left: 120px;
    }

    #sec{
        position:absolute;
        /* top: 30px; */
        left: 400px;

    }

    #end{
        position: absolute;
        left: 1240px;

    }

    #text3{
        background-color: #F7CECE;
    }

    .switch{
        position: absolute;
        right: 30px;
        top:150px;
    }

</style>