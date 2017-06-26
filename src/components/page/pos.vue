<template>
  <div class="pos">
    <el-row >
        <el-col :span='7' class='pos-order'>
        我是订单栏
        </el-col>
        <!--商品展示-->
        <el-col :span="17">
          我是产品栏
        </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'pos'  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .pos-order{
    background-color:#F9AFC;
    border-right:1px solid #COCCDA;
  }
</style>
