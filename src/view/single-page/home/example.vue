<template>
    <div ref="dom"></div>
</template>

<script>
import echarts from 'echarts'
import { on, off } from '@/libs/tools'
export default {
  name: 'serviceRequests',
  props: ['echartsData'],
  data () {
    return {
      dom: null,
      dataName: ['iai', 'hpe', 'qty'],
      option: {
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross',
            label: {
              backgroundColor: '#6a7985'
            }
          }
        },
        grid: {
          top: '3%',
          left: '1.2%',
          right: '1%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: [
          {
            type: 'category',
            boundaryGap: false,
            data: []
          }
        ],
        yAxis: [
          {
            type: 'value'
          }
        ],
        series: [
          {
            name: 'iAI',
            type: 'line',
            areaStyle: { normal: {
              color: '#2d8cf0'
            } },
            data: []
          },
          {
            name: 'HPE',
            type: 'line',
            areaStyle: { normal: {
              color: '#10A6FF'
            } },
            data: []
          },
          {
            name: 'QTY',
            type: 'line',
            areaStyle: { normal: {
              color: '#0C17A6'
            } },
            data: []
          },
        ]
      }
    }
  },
  methods: {
    resize () {
      this.dom.resize()
    },
    updateChart() {
      this.$nextTick(() => {
        this.dom = echarts.init(this.$refs.dom)
        this.dom.setOption(this.option)
        on(window, 'resize', this.resize)
      })
    },
    mergeData(data, name) {
      return data.map((item) => {
        return item[name];
      })
    }
  },
  watch: {
    echartsData: {
      immediate: true, // 将立即以表达式的当前值触发回调,
      deep: true,
      handler (val) {
        this.option.xAxis[0].data = val.map((data) => {
          return data.date;
        });
        for(let i = 0; i < this.dataName.length; i++) {
          let name = this.dataName[i];
          this.option.series[i].data = this.mergeData(val, name);
        }
        this.updateChart();
      }
    },
  },
  mounted () {

    this.updateChart();
  },
  beforeDestroy () {
    off(window, 'resize', this.resize)
  }
}
</script>
