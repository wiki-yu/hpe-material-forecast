<template>
  <div>
 <Row style="padding-top: 10px">
      <Col span="24" style="padding-right: 5px" >
      <Card>
        <p slot="title" class="card-title" >
          <Icon type="android-wifi"></Icon>
          Material table
        <div style="height: 50px">
        <Dropdown style="margin-left: 20px">
          <Button type="primary">
              Material
              <Icon type="ios-arrow-down"></Icon>
          </Button>
          <DropdownMenu slot="list">
            <DropdownItem v-for="n in 6" :key="n" @click.native="handleClick(n)">Material{{n}}</DropdownItem>
          </DropdownMenu>
        </Dropdown>
        </div>
        </p>
        <div style="height: 200px">
          <!-- <Table stripe :columns="columns1" :data="data"></Table> -->
          <Table height="200" :columns="columns1" :data="data"></Table>
        </div>
      </Card>
      </Col>
    </Row>

    <Row>
      <Card shadow>
        <example style="height: 310px;" :echartsData="data"  />
      </Card>
    </Row>
  </div>
</template>

<script>
import InforCard from '_c/info-card'
import CountTo from '_c/count-to'
import { ChartPie, ChartBar } from '_c/charts'
import Example from './example.vue'
export default {
  name: 'home',
  components: {
    InforCard,
    CountTo,
    ChartPie,
    ChartBar,
    Example
  },
  data () {
    return {
      inforCardData: [
        { title: '新增用户', icon: 'md-person-add', count: 803, color: '#2d8cf0' },
        { title: '累计点击', icon: 'md-locate', count: 232, color: '#19be6b' },
        { title: '新增问答', icon: 'md-help-circle', count: 142, color: '#ff9900' },
        { title: '分享统计', icon: 'md-share', count: 657, color: '#ed3f14' },
        { title: '新增互动', icon: 'md-chatbubbles', count: 12, color: '#E46CBB' },
        { title: '新增页面', icon: 'md-map', count: 14, color: '#9A66E4' }
      ],
      pieData: [
        { value: 335, name: '直接访问' },
        { value: 310, name: '邮件营销' },
        { value: 234, name: '联盟广告' },
        { value: 135, name: '视频广告' },
        { value: 1548, name: '搜索引擎' }
      ],
      barData: {
        Mon: 13253,
        Tue: 34235,
        Wed: 26321,
        Thu: 12340,
        Fri: 24643,
        Sat: 1322,
        Sun: 1324
      },
      columns1: [
        {
          title: 'Date',
          key: 'date'
        },
        {
          title: 'iAI',
          key: 'iai'
        },
        {
          title: 'HPE',
          key: 'hpe'
        },
        {
          title: 'QTY',
          key: 'qty'
        }
      ],
      data: [],
      data1: [
        {  
          date: '2020-08-03',
          iai: 866,
          hpe: 2771,
          qty: 196
        },
        {  
          date: '2020-08-10',
          iai: 751,
          hpe: 2806,
          qty: 704
        },
        {  
          date: '2020-08-17',
          iai: 670,
          hpe: 2180,
          qty: 136
        },
        {  
          date: '2020-08-24',
          iai: 787,
          hpe: 2180,
          qty: 300
        }
      ],
      data2: [
        {  
          date: '2020-08-03',
          iai: 50,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-10',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-17',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-24',
          iai: 10,
          hpe: 11,
          qty: 12
        }
      ],
      data3: [
        {  
          date: '2020-08-03',
          iai: 10,
          hpe: 11,
          qty: 120
        },
        {  
          date: '2020-08-10',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-17',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-24',
          iai: 10,
          hpe: 11,
          qty: 12
        }
      ],
      data4: [
        {  
          date: '2020-08-03',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-10',
          iai: 10,
          hpe: 101,
          qty: 12
        },
        {  
          date: '2020-08-17',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-24',
          iai: 10,
          hpe: 11,
          qty: 12
        }
      ],
      data5: [
        {  
          date: '2020-08-03',
          iai: 10,
          hpe: 11,
          qty: 102
        },
        {  
          date: '2020-08-10',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-17',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-24',
          iai: 10,
          hpe: 11,
          qty: 12
        }
      ],
      data6: [
        {  
          date: '2020-08-03',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-10',
          iai: 10,
          hpe: 11,
          qty: 120
        },
        {  
          date: '2020-08-17',
          iai: 10,
          hpe: 11,
          qty: 12
        },
        {  
          date: '2020-08-24',
          iai: 10,
          hpe: 11,
          qty: 12
        }
      ]
    }
  },
  mounted () {
    this.data = this.data1;
  },
  methods: {
    handleClick(index) {
      this.test = index;
      this.data = this[`data${index}`]
    }
  }
}
</script>

<style lang="less">
.count-style{
  font-size: 50px;
}
</style>
