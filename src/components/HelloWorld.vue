<template>
  <div class="home">
       <!-- 为ECharts准备一个具备大小（宽高）的Dom -->
    <div style="height: 1000px; width:1000px;" ref = "chart1"></div>  
  </div>  
</template>

<script>
    import echarts from 'echarts'
    import geodata from './geodata'
    import "echarts/map/js/china.js"
    export default {
        name: 'Home',
        data() {
            return {
                list: "2",
                geoCoordMap:geodata,
                data:[  {name: '广州', value: 38},
          {name: '延安', value: 38},
          {name: '太原', value: 39},
          {name: '清远', value: 39},
          {name: '中山', value: 39},
          {name: '昆明', value: 39},
          {name: '寿光', value: 40},
          {name: '盘锦', value: 40},
          {name: '长治', value: 41},
          {name: '深圳', value: 41},
          {name: '珠海', value: 42},
          {name: '宿迁', value: 100},]
            }
        },
        methods: {
          convertData(data) {
            let res = []
            for (let i = 0; i < data.length; i++) {
              let geoCoord = this.geoCoordMap[data[i].name];
              if (geoCoord) {
                res.push({
                  name: data[i].name,
                  value: geoCoord.concat(data[i].value)
                })
              }
            }
            return res
          },
            initChart() {
                // 基于准备好的dom，初始化echarts实例
                var myChart = echarts.init(this.$refs.chart1);
                // 指定图表的配置项和数据
                var option = {
                    title: {
                        text: "国内疫情"
                    },
                    tooltip: {
                        trigger: 'item'
                    },
                    geo: {
                        map: 'china',
                         label: {
                            normal: {
                              show: true,
                              textStyle: {
                                color: 'rgb(249, 249, 249)',
                                fontSize: 10,
                              },
                            },
                            emphasis: {
                              show: true,
                              textStyle: {
                                color: 'rgb(249, 249, 249)',
                                fontSize: 14,
                              },
                            },
                          },
                        itemStyle: {
                          normal: {
                            label: { show: true },
                            areaColor: '#2f82ce',
                            borderColor: '#0DAAC1',
                          },
                          emphasis: {
                            label: { show: true },
                            areaColor: '#2f55ce',
                          },
                        },
                      },
                    series: [{
                        name: '确诊数量',
                        type: 'effectScatter',
                        coordinateSystem: 'geo',
                        symbolSize: function (data) {
                          return Math.sqrt(data[2]);
                      },
                        data: this.convertData(this.data)
                    }]
                }

                // 使用刚指定的配置项和数据显示图表
                myChart.setOption(option)
            }
        },
        mounted() {
            this.initChart();
        }

    }
</script>


<style scoped>

</style>