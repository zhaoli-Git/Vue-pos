<template>
  <div class="pos">
    <el-row>
        <el-col :span='7' class='pos-order' id='order-list'>
          <el-tabs>
            <el-tab-pane label="点餐" name="first">
              <el-table :data="tableData"  style="width: 100%">
                <el-table-column
                  prop="goodsName"
                  label="商品名称">
                </el-table-column>
                <el-table-column
                  prop="count"
                  label="数量">
                </el-table-column>
                <el-table-column
                  prop="price"
                  label="金额">
                </el-table-column>
                <el-table-column
                  label="操作" width="100">
                  <template scope="scope">
                    <el-button type="text" size="small">删除</el-button>
                    <el-button type="text" size="small">增加</el-button>        
                  </template>
                </el-table-column>
              </el-table>
              <div class='btn-group'>
                <el-button type='warning'>挂单</el-button>
                <el-button type='info'>删除</el-button>
                <el-button type='success'>结账</el-button>
              </div>
            </el-tab-pane>
            <el-tab-pane label="挂单" name="second">挂单</el-tab-pane>
            <el-tab-pane label="外卖" name="third">外卖</el-tab-pane>
          </el-tabs>
        </el-col>
        <!--商品展示-->
        <el-col :span="17" id='order-right'>
          <div class="often-goods">
            <div class="title">常用商品</div>
            <div class="often-goods-list">
              <ul>
                <li v-for='item in oftenGoods'>
                  <span>{{item.goodsName}}</span>
                  <span class="o-price">￥{{item.price}}元</span>
                </li>
              </ul>
            </div>
          </div> 
          <div class="goods-type">
            <el-tabs>
              <el-tab-pane label="汉堡">
                <ul class='cookList'>
                  <li v-for='item in type0Goods'>
                      <span class="foodImg"><img v-bind:src="item.goodsImg" width="100%"></span>
                      <i class='i-group'>
                        <i class="foodName">{{item.goodsName}}</i>
                        <i class="foodPrice">￥{{item.price}}元</i>
                      </i> 
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="小食">
                <ul class='cookList'>
                  <li v-for='item in type1Goods'>
                      <span class="foodImg"><img v-bind:src="item.goodsImg" width="100%"></span>
                      <i class='i-group'>
                        <i class="foodName">{{item.goodsName}}</i>
                        <i class="foodPrice">￥{{item.price}}元</i>
                      </i> 
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="饮料">
                <ul class='cookList'>
                  <li v-for='item in type2Goods'>
                      <span class="foodImg"><img v-bind:src="item.goodsImg" width="100%"></span>
                      <i class='i-group'>
                        <i class="foodName">{{item.goodsName}}</i>
                        <i class="foodPrice">￥{{item.price}}元</i>
                      </i> 
                  </li>
                </ul>
              </el-tab-pane>
              <el-tab-pane label="套餐">
                <ul class='cookList'>
                  <li v-for='item in type3Goods'>
                      <span class="foodImg"><img v-bind:src="item.goodsImg" width="100%"></span>
                      <i class='i-group'>
                        <i class="foodName">{{item.goodsName}}</i>
                        <i class="foodPrice">￥{{item.price}}元</i>
                      </i> 
                  </li>
                </ul>
              </el-tab-pane>       
            </el-tabs>
          </div>
        </el-col>
    </el-row>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'pos',
  data() {
    return {
      tableData: [{
          
          goodsName: '可口可乐',
          price: 8,
          count:1
        }, {
          
          goodsName: '香辣鸡腿堡',
          price: 15,
          count:1
        }, {
         
          goodsName: '爱心薯条',
          price: 8,
          count:1
        }, {
         
          goodsName: '甜筒',
          price: 8,
          count:1
        }],
        oftenGoods:[
          // {
          //     goodsId:1,
          //     goodsName:'香辣鸡腿堡',
          //     price:18
          // }, {
          //     goodsId:2,
          //     goodsName:'田园鸡腿堡',
          //     price:15
          // }, {
          //     goodsId:3,
          //     goodsName:'和风汉堡',
          //     price:15
          // }, {
          //     goodsId:4,
          //     goodsName:'快乐全家桶',
          //     price:80
          // }, {
          //     goodsId:5,
          //     goodsName:'脆皮炸鸡腿',
          //     price:10
          // }, {
          //     goodsId:6,
          //     goodsName:'魔法鸡块',
          //     price:20
          // }, {
          //     goodsId:7,
          //     goodsName:'可乐大杯',
          //     price:10
          // }, {
          //     goodsId:8,
          //     goodsName:'雪顶咖啡',
          //     price:18
          // }, {
          //     goodsId:9,
          //     goodsName:'大块鸡米花',
          //     price:15
          // }, {
          //     goodsId:20,
          //     goodsName:'香脆鸡柳',
          //     price:17
          // }
          
      ],
       type0Goods:[
          // {
          //     goodsId:1,
          //     goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
          //     goodsName:'香辣鸡腿堡',
          //     price:18
          // }, {
          //     goodsId:2,
          //     goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
          //     goodsName:'田园鸡腿堡',
          //     price:15
          // }, {
          //     goodsId:3,
          //     goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
          //     goodsName:'和风汉堡',
          //     price:15
          // }, {
          //     goodsId:4,
          //      goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
          //     goodsName:'快乐全家桶',
          //     price:80
          // }, {
          //     goodsId:5,
          //      goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
          //     goodsName:'脆皮炸鸡腿',
          //     price:10
          // }, {
          //     goodsId:6,
          //      goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
          //     goodsName:'魔法鸡块',
          //     price:20
          // }, {
          //     goodsId:7,
          //      goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
          //     goodsName:'可乐大杯',
          //     price:10
          // }, {
          //     goodsId:8,
          //      goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
          //     goodsName:'雪顶咖啡',
          //     price:18
          // }, {
          //     goodsId:9,
          //      goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
          //     goodsName:'大块鸡米花',
          //     price:15
          // }, {
          //     goodsId:20,
          //      goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
          //     goodsName:'香脆鸡柳',
          //     price:17
          // }
          
      ],
      type1Goods:[],
      type2Goods:[],
      type3Goods:[]
    }
  }, 
  created(){
    axios.get('http://jspang.com/DemoApi/oftenGoods.php')
    .then(response=>{
        console.log(response);
        this.oftenGoods=response.data;
    })
    .catch(error=>{
        console.log(error);
        alert('网络错误，不能访问');
    })
    
    axios.get('http://jspang.com/DemoApi/typeGoods.php')
      .then(response=>{
         console.log(response);
         //this.oftenGoods=response.data;
         this.type0Goods=response.data[0];
         this.type1Goods=response.data[1];
         this.type2Goods=response.data[2];
         this.type3Goods=response.data[3];
 
      })
      .catch(error=>{
          console.log(error);
          alert('网络错误，不能访问');
      })
  }, 
  mounted:function(){
    var orderHeight=document.body.clientHeight;
    document.getElementById("order-list").style.height=orderHeight+'px';
  } 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .pos-order{
    background-color:#F9FAFC;
    border-right:1px solid #COCCDA;
  }
  .btn-group{
    margin-top:20px;
  }
  .title{
      height: 21px;
      border-bottom:1px solid #D3DCE6;
      background-color: #F9FAFC;
      padding:10px;
      font-size:14px;
   }
   .often-goods-list ul li{
      list-style: none;
      float:left;
      border:1px solid #E5E9F2;
      padding:10px;
      margin:5px;
      background-color:#fff;
   }
  .o-price{
      color:#58B7FF; 
   }
   .goods-type{
     float:left;
   }
  .cookList li{
        list-style: none;
        width:23%;
        border:1px solid #E5E9F2;
        height: auto;
        overflow: hidden;
        background-color:#fff;
        padding: 2px;
        float:left;
        margin: 2px;
        text-align:center;
    }
  .cookList li span{
      
        display: block;
        float:left;
        // text-align:center;
  }
  .cookList li .i-group{
      font-style:normal;
      font-size:10px;
      float:right;
      width:60%;
      padding-top:14px;
  }
   .cookList li .i-group i{
     font-style:normal;
     display:block;
   }
  .foodImg{
      width: 40%;
    
  }
  .foodName{
      font-size: 18px;
      padding-left: 5px;
      color:brown;
      
  }
  .foodPrice{
      font-size: 16px;
      padding-left: 10px;
      padding-top:10px;
  }
 
  .el-tab-pane ul{
    list-style:none;
    float:left;
  }
</style>
