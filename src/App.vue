<template>
  <div id="app1">
    <p>第一次修改</p>
    <img src="./assets/vn.jpg">
    <p :class="{active:behavior}" @click="fun()">{{a}}</p>
    <div id="echarts" :style="{width: '326px', height: '250px', border: '1px solid red',position:'relative',left:'50%' }"></div>
    <div id="echarts0" :style="{width: '326px', height: '250px', border: '1px solid red',position:'relative',left:'50%' }"></div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      a:"111",
      behavior:true,
    };
  },
  methods:{
  fun(){
    this.behavior =!this.behavior;
  },

  //vn成长攻击力
  drawLine() {
      // 基于准备好的dom，初始化echarts实例
      var myChart = this.$echarts.init(document.getElementById("echarts"));
      // 绘制图表
       var option = {
       xAxis: {
        // type: 'category',
        data: ['2', '4', '6', '8', '10', '12', '14']
       },
       yAxis: {
        type: 'value'
       },
        legend: {
        show:true,
        icon:'pie',
        orient:'horizontal',
        data:[{
            name:'薇恩成长攻击力',
            icon:'image://./assets/timg.jpg',//格式为'image://+icon文件地址'，其中image::后的//不能省略
        },],
        },
       grid: {
        left:'20%',
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
    //装备攻击力叠加图
    drawLine0(){
    // 基于准备好的dom，初始化echarts实例
    var myChart = this.$echarts.init(document.getElementById("echarts0"));
    var  option = {
    title: {
        text: '堆叠区域图',
        show:false,
    },
    tooltip : {
        trigger: 'axis',
        axisPointer: {
            type: 'cross',
            label: {
                backgroundColor: '#6a7985'
            }
        }
    },
    legend: {
        data:['邮件营销','联盟广告','视频广告','直接访问','搜索引擎']
    },
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
    },
    xAxis : [
        {
            type : 'category',
            boundaryGap : false,
            data : ['周一','周二','周三','周四','周五','周六','周日']
        }
    ],
    yAxis : [
        {
            type : 'value'
        }
    ],
    series : [
        {
            name:'邮件营销',
            type:'line',
            stack: '总量',
            areaStyle: {},
            data:[120, 132, 101, 134, 90, 230, 210]
        },
        {
            name:'联盟广告',
            type:'line',
            stack: '总量',
            areaStyle: {},
            data:[220, 182, 191, 234, 290, 330, 310]
        },
        {
            name:'视频广告',
            type:'line',
            stack: '总量',
            areaStyle: {},
            data:[150, 232, 201, 154, 190, 330, 410]
        },
        {
            name:'直接访问',
            type:'line',
            stack: '总量',
            areaStyle: {normal: {}},
            data:[320, 332, 301, 334, 390, 330, 320]
        },
        {
            name:'搜索引擎',
            type:'line',
            stack: '总量',
            label: {
                normal: {
                    show: true,
                    position: 'top'
                }
            },
            areaStyle: {normal: {}},
            data:[820, 932, 901, 934, 1290, 1330, 1320]
        }
    ]
    };
    myChart.setOption(option);
    },
    },
  mounted(){
  this.drawLine();
  this.drawLine0();
  var _this =this;
  console.log(_this.drawLine());
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
.active{
  color:blue;
}
</style>
