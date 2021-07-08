<template>
  <!-- 评审专家画像 -->
  <div class="box">
    <div class="charts" ref="radarchart">
    </div>
  </div>
</template>
<script>


export default {
  name: 'dull',
  data() {
    return {
      chartInstance: null,
      list: null
    }
  },
  mounted() {
    this.initChart()
    this.getData()
  },
  methods: {
    // 初始化echartsInstance对象
    initChart() {
      this.chartInstance = this.$echarts.init(this.$refs.radarchart)
    },
    // 获取数据
    getData() {
      // 加强接口渲染
      // const {data:ret} = await this.$http.get('')
      const data = [{ name: '1', value: '1' }, { name: '2', value: '2' }]
      console.log(data);
      this.list = data
      this.updateData()
    },
    // 更新数据
    updateData() {
      const option = {
        title: {
          text: '呆滞项目物资分析',
          left: 'center',
          padding: [15, 0, 10, 0],
          textStyle: {
            color: '#FFFFFF'
          }
        },
        tooltip: {
          trigger: 'item',
          formatter: '{b}:{d}%'
        },
        legend: {
          top: 'bottom'
        },
        series: [
          {
            type: 'pie',
            radius: [50, 250],
            center: ['50%', '50%'],
            roseType: 'area',
            itemStyle: {
              borderRadius: 8
            },
            data: [
              { value: 40, name: 'rose 1' },
              { value: 38, name: 'rose 2' },
              { value: 32, name: 'rose 3' },
              { value: 30, name: 'rose 4' },
              { value: 28, name: 'rose 5' },
              { value: 26, name: 'rose 6' },
              { value: 22, name: 'rose 7' },
              { value: 18, name: 'rose 8' }
            ]
          }
        ]
      }
      this.chartInstance.setOption(option)
    }
  }
}
</script>
<style scoped>
.box {
  margin: 1.25rem 0.9375rem;
  width: 47.5rem;
  height: 43.125rem;
  border: 1px solid black;
  background: pink;
}
.charts {
  width: 47.5rem;
  height: 43.125rem;
}
</style>
