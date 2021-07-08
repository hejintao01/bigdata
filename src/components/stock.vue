<template>
  <!-- 评审专家画像 -->
  <div class="box">
    <div class="charts" ref="radarchart">
    </div>
  </div>
</template>
<script>


export default {
  name: 'stock',
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
          text: '库存占比分析',
          left: 'center',
          padding: [15, 0, 10, 0],
          textStyle: {
            color: '#FFFFFF'
          }
        },
        tooltip: {
          trigger: 'item',
          formatter: " {b}：{c} "

          // ({d}%)   代表该模块所占圆环比例
          // formatter: "{a} <br/>{b}: {c} ({d}%)"
        },
        legend: {
          top: 'bottom',
        },
        // 设置环形中间的数据。默认center为中间，如果图表位置变化了，中间文字是不变的
        graphic: [{
          type: 'text',
          left: 'center',
          top: '40%',
          style: {
            fill: '#686868',
            text: '库存总量'
          }
        }, {
          type: 'text',
          left: 'center',
          top: '50%',
          z: 10,
          style: {
            text: '3231',
            font: '30px Microsoft YaHei'
          }
        }],
        //环形颜色
        // color: ['#ffb616', '#ccc'],
        series: [

          {
            type: 'pie',
            radius: ['30%', '40%'],
            labelLine: {
              normal: {
                length: 20,
                length2: 70,
                lineStyle: {
                  color: '#333'
                }
              }

            },
            label: {
              normal: {
                // \n\n可让文字居于牵引线上方，很关键
                //  {b}  代表显示的内容标题
                // {c}代表数据
                formatter: ' {b}：{c} \n\n',

                borderWidth: 20,
                borderRadius: 4,
                padding: [0, -70],
                rich: {
                  a: {
                    color: '#333',
                    fontSize: 12,
                    lineHeight: 20
                  },
                  b: {
                    fontSize: 12,
                    lineHeight: 20,
                    color: '#333'
                  }
                }
              }
            },
            data: [{ value: 1048, name: '搜索引擎' },
            { value: 735, name: '直接访问' },
            { value: 580, name: '邮件营销' },
            { value: 484, name: '联盟广告' },
            { value: 300, name: '视频广告' }]
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
