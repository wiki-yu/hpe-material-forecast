<template>
  <div>
 <Row style="padding-top: 10px">
      <Col span="24" style="padding-right: 5px" >
      <Card>
        <p slot="title" class="card-title" >
          <Icon type="android-wifi"></Icon>
          Material table
        <div style="height: 50px">
        <Dropdown style="margin-left: 2px">
          <Button type="primary">
              {{curName}}
              <Icon type="ios-arrow-down"></Icon>
          </Button>
          <DropdownMenu slot="list">
            <DropdownItem v-for="n in 2" :key="n" @click.native="handleClick(n)">{{getName(n)}}</DropdownItem>
          </DropdownMenu>
        </Dropdown>
        </div>
        </p>
        <div style="height: 300px">
          <!-- <Table stripe :columns="columns1" :data="data"></Table> -->
          <Table height="300" :columns="columns1" :data="data"></Table>
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
      curIndex: 1,
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
      data1: {
        name: 'A',
        data: [
          {
            date: '2020-07-20',
            iai: 592,
            hpe: 901,
            qty: 572
          },
          {
            date: '2020-07-27',
            iai: 881,
            hpe: 1432,
            qty: 310
          },
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
        ]
      },
      data2: {
        name: 'B',
        data: [
          {
            date: '2020-07-20',
            iai: 15,
            hpe: 58,
            qty: 13
          },
          {
            date: '2020-07-27',
            iai: 12,
            hpe: 62,
            qty: 35
          },
          {
            date: '2020-08-03',
            iai: 12,
            hpe: 78,
            qty: 5
          },
          {
            date: '2020-08-10',
            iai: 12,
            hpe: 57,
            qty: 21
          },
          {
            date: '2020-08-17',
            iai: 13,
            hpe: 31,
            qty: 24
          },
          {
            date: '2020-08-24',
            iai: 12,
            hpe: 27,
            qty: 10
          }
        ]
      },
      // data3: [
      //   {
      //     date: '2020-07-20',
      //     iai: 4,
      //     hpe: 25,
      //     qty: 7
      //   },
      //   {
      //     date: '2020-07-27',
      //     iai: 4,
      //     hpe: 20,
      //     qty: 0
      //   },
      //   {
      //     date: '2020-08-03',
      //     iai: 4,
      //     hpe: 8,
      //     qty: 2
      //   },
      //   {
      //     date: '2020-08-10',
      //     iai: 4,
      //     hpe: 7,
      //     qty: 8
      //   },
      //   {
      //     date: '2020-08-17',
      //     iai: 4,
      //     hpe: 8,
      //     qty: 6
      //   },
      //   {
      //     date: '2020-08-24',
      //     iai: 4,
      //     hpe: 8,
      //     qty: 4
      //   }
      // ],
      // data4: [
      //   {
      //     date: '2020-07-20',
      //     iai: 1,
      //     hpe: 26,
      //     qty: 0
      //   },
      //   {
      //     date: '2020-07-27',
      //     iai: 1,
      //     hpe: 26,
      //     qty: 0
      //   },
      //   {
      //     date: '2020-08-03',
      //     iai: 1,
      //     hpe: 26,
      //     qty: 0
      //   },
      //   {
      //     date: '2020-08-10',
      //     iai: 2,
      //     hpe: 16,
      //     qty: 0
      //   },
      //   {
      //     date: '2020-08-17',
      //     iai: 2,
      //     hpe: 32,
      //     qty: 0
      //   },
      //   {
      //     date: '2020-08-24',
      //     iai: 2,
      //     hpe: 32,
      //     qty: 0
      //   }
      // ],
      // data5: [
      //   {
      //     date: '2020-07-20',
      //     iai: 8,
      //     hpe: 16,
      //     qty: 8
      //   },
      //   {
      //     date: '2020-07-27',
      //     iai: 7,
      //     hpe: 15,
      //     qty: 2
      //   },
      //   {
      //     date: '2020-08-03',
      //     iai: 7,
      //     hpe: 12,
      //     qty: 16
      //   },
      //   {
      //     date: '2020-08-10',
      //     iai: 11,
      //     hpe: 7,
      //     qty: 16
      //   },
      //   {
      //     date: '2020-08-17',
      //     iai: 8,
      //     hpe: 7,
      //     qty: 8
      //   },
      //   {
      //     date: '2020-08-24',
      //     iai: 7,
      //     hpe: 7,
      //     qty: 7
      //   }
      // ],
      // data6: [
      //   {
      //     date: '2020-07-20',
      //     iai: 259,
      //     hpe: 446,
      //     qty: 206
      //   },
      //   {
      //     date: '2020-07-27',
      //     iai: 98,
      //     hpe: 432,
      //     qty: 92
      //   },
      //   {
      //     date: '2020-08-03',
      //     iai: 89,
      //     hpe: 412,
      //     qty: 70
      //   },
      //   {
      //     date: '2020-08-10',
      //     iai: 349,
      //     hpe: 385,
      //     qty: 40
      //   },
      //   {
      //     date: '2020-08-17',
      //     iai: 242,
      //     hpe: 738,
      //     qty: 42
      //   },
      //   {
      //     date: '2020-08-24',
      //     iai: 229,
      //     hpe: 722,
      //     qty: 123
      //   }
      // ]
    }
  },
  mounted () {
    this.data = this.data1.data
  },
  computed: {
    curName() {
      return this[`data${this.curIndex}`].name;
    }
  },
  methods: {
    handleClick(index) {
      this.curIndex = index
      this.data = this[`data${index}`].data
    },
    getName(index) {
      return this[`data${index}`].name;
    }
  }
}
</script>

<style lang="less">
.count-style{
  font-size: 50px;
}
</style>
