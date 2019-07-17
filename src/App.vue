<template>
  <div id="app1">
    <p>第一次修改</p>
    <img src="./assets/logo.png">
    <p>{{a}}</p>
    <div id="echarts" :style="{width: '326px', height: '250px', border: '1px solid red',position:'relative',left:'50%' }"></div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      a:"111",
    };
  },
  methods:{
  drawLine() {
      // 基于准备好的dom，初始化echarts实例
      var myChart = this.$echarts.init(document.getElementById("echarts"));
      // 绘制图表
       var option = {
       xAxis: {
        type: 'category',
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
       },
       yAxis: {
        type: 'value'
       },
        legend: {
             show:true,
        orient:'horizontal',
        data:[ {
            name:'薇恩成长攻击力',
            // textStyle:{
            //     fontSize:12,
            //     fontWeight:'bolder',
            //     color:'#cccccc'
            // },
            // icon:'image://./assets/logo.png'//格式为'image://+icon文件地址'，其中image::后的//不能省略
        },]

        },
       grid: {
        left:'20%',
        // show:true,
        // borderColor:'yellow',
        tooltip: {
         show:true,
        },
        },
       series: [{
        name:'薇恩成长攻击力',
        data: [820, 932, 901, 934, 1290, 1330, 1320],
        type: 'line'
       }]
       };

      // 为echarts对象加载数据
      myChart.setOption(option);
    },
  },
  mounted(){
  this.drawLine();
  }
}
</script>

<style>
#app1 {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
