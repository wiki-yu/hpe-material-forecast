<template>
  <div>

    <Row style="padding-top: 10px">
      <Col span="24" style="padding-right: 5px" >
        <Card>
          <p slot="title" class="card-title" >
            <Icon type="android-wifi"></Icon>
            Material Table
            <div style="height: 50px">
              <Dropdown style="margin-left: 2px">
                <Button type="primary">
                    {{curName}}
                    <Icon type="ios-arrow-down"></Icon>
                </Button>
                <DropdownMenu slot="list">
                  <DropdownItem v-for="n in 6" :key="n" @click.native="handleClick(n)">{{getName(n)}}</DropdownItem>
                </DropdownMenu>
              </Dropdown>
            </div>
          </p>
          <div style="height: 150px">
            <!-- <Table stripe :columns="columns1" :data="data"></Table> -->
            <Table height="150" :columns="columns1" :data="data"></Table>
          </div>
        </Card>
      </Col>
    </Row>

    <Row style="padding-top: 10px">
      <Card shadow>
        <p slot="title" class="card-title" >
          <Icon type="android-wifi"></Icon>
          Material Chart
        </p>
        <example style="height: 200px;" :echartsData="data"  />
      </Card>
    </Row>

    <Row style="padding-top: 10px">
      <div>
        <Card title="Export EXCEL">
          <Row>
          <Button icon="md-download" :loading="exportLoading" @click="exportExcel">Export File</Button>
          </Row>
        </Card>
      </div>
    </Row>
  </div>
</template>

<script>
import InforCard from '_c/info-card'
import CountTo from '_c/count-to'
import { ChartPie, ChartBar } from '_c/charts'
import Example from './example.vue'
import excel from '@/libs/excel'
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
      exportLoading: false,

      columns1: [
        {
          title: 'Week (starting on)',
          key: 'date'
        },
        {
          title: 'iAI Prediction',
          key: 'iai'
        },
        {
          title: 'HPE Lead-Time Forecast',
          key: 'hpe'
        },
        {
          title: 'Actual Requirement QTY',
          key: 'qty'
        }
      ],
      data: [],
      data1: {
        name: '840759-091',
        data: [
          {
            date: '2020-06-01',
            iai: 1524,
            hpe: 1969,
            qty: 180
          },
          {
            date: '2020-06-08',
            iai: 1283,
            hpe: 1925,
            qty: 434
          },
          {
            date: '2020-06-15',
            iai: 1327,
            hpe: 1925,
            qty: 2640
          },
          {
            date: '2020-06-22',
            iai: 1059,
            hpe: 721,
            qty: 436
          },
          {
            date: '2020-06-29',
            iai: 1011,
            hpe: 1241,
            qty: 488
          },
          {
            date: '2020-07-06',
            iai: 835,
            hpe: 659,
            qty: 976
          },
          {
            date: '2020-07-13',
            iai: 865,
            hpe: 659,
            qty: 370
          },
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
            qty: 234
          },
          {
            date: '2020-08-31',
            iai: 443,
            hpe: 688,
            qty: 148
          },
          {
            date: '2020-09-07',
            iai: 370,
            hpe: 635,
            qty: 148
          },
          {
            date: '2020-09-14',
            iai: 733,
            hpe: 626,
            qty: NaN
          }
        ]
      },
      data2: {
        name: '870660-001',
        data: [
          {
            date: '2020-06-01',
            iai: 6,
            hpe: 30,
            qty: 8
          },
          {
            date: '2020-06-08',
            iai: 6,
            hpe: 30,
            qty: 4
          },
          {
            date: '2020-06-15',
            iai: 6,
            hpe: 46,
            qty: 4
          },
          {
            date: '2020-06-22',
            iai: 15,
            hpe: 55,
            qty: 10
          },
          {
            date: '2020-06-29',
            iai: 11,
            hpe: 59,
            qty: 10
          },
          {
            date: '2020-07-06',
            iai: 10,
            hpe: 40,
            qty: 0
          },
          {
            date: '2020-07-13',
            iai: 13,
            hpe: 50,
            qty: 12
          },
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
            qty: 4
          },
          {
            date: '2020-08-31',
            iai: 11,
            hpe: 25,
            qty: 73
          },
          {
            date: '2020-09-07',
            iai: 11,
            hpe: 33,
            qty: 4
          },
          {
            date: '2020-09-14',
            iai: 15,
            hpe: 29,
            qty: NaN
          }
        ]
      },
      data3: {
        name: '877688-001',
        data: [
          {
            date: '2020-06-01',
            iai: 8,
            hpe: 49,
            qty: 0
          },
          {
            date: '2020-06-08',
            iai: 8,
            hpe: 21,
            qty: 5
          },
          {
            date: '2020-06-15',
            iai: 8,
            hpe: 21,
            qty: 5
          },
          {
            date: '2020-06-22',
            iai: 8,
            hpe: 22,
            qty: 0
          },
          {
            date: '2020-06-29',
            iai: 4,
            hpe: 15,
            qty: 0
          },
          {
            date: '2020-07-06',
            iai: 4,
            hpe: 26,
            qty: 2
          },
          {
            date: '2020-07-13',
            iai: 4,
            hpe: 26,
            qty: 0
          },
          {
            date: '2020-07-20',
            iai: 4,
            hpe: 25,
            qty: 7
          },
          {
            date: '2020-07-27',
            iai: 4,
            hpe: 20,
            qty: 0
          },
          {
            date: '2020-08-03',
            iai: 4,
            hpe: 8,
            qty: 2
          },
          {
            date: '2020-08-10',
            iai: 4,
            hpe: 7,
            qty: 8
          },
          {
            date: '2020-08-17',
            iai: 4,
            hpe: 8,
            qty: 6
          },
          {
            date: '2020-08-24',
            iai: 4,
            hpe: 8,
            qty: 6
          },
          {
            date: '2020-08-31',
            iai: 4,
            hpe: 4,
            qty: 0
          },
          {
            date: '2020-09-07',
            iai: 90,
            hpe: 7,
            qty: 0
          },
          {
            date: '2020-09-14',
            iai: 11,
            hpe: 8,
            qty: NaN
          }
        ]
      },
      data4: {
        name: 'C8S92-62001',
        data: [
          {
            date: '2020-06-01',
            iai: 3,
            hpe: 29,
            qty: 0
          },
          {
            date: '2020-06-08',
            iai: 2,
            hpe: 26,
            qty: 0
          },
          {
            date: '2020-06-15',
            iai: 2,
            hpe: 26,
            qty: 0
          },
          {
            date: '2020-06-22',
            iai: 1,
            hpe: 24,
            qty: 0
          },
          {
            date: '2020-06-29',
            iai: 1,
            hpe: 23,
            qty: 0
          },
          {
            date: '2020-07-06',
            iai: 1,
            hpe: 26,
            qty: 0
          },
          {
            date: '2020-07-13',
            iai: 1,
            hpe: 26,
            qty: 0
          },
          {
            date: '2020-07-20',
            iai: 1,
            hpe: 26,
            qty: 0
          },
          {
            date: '2020-07-27',
            iai: 1,
            hpe: 26,
            qty: 0
          },
          {
            date: '2020-08-03',
            iai: 1,
            hpe: 26,
            qty: 0
          },
          {
            date: '2020-08-10',
            iai: 2,
            hpe: 16,
            qty: 0
          },
          {
            date: '2020-08-17',
            iai: 2,
            hpe: 32,
            qty: 0
          },
          {
            date: '2020-08-24',
            iai: 2,
            hpe: 32,
            qty: 0
          },
          {
            date: '2020-08-31',
            iai: 2,
            hpe: 20,
            qty: 0
          },
          {
            date: '2020-09-07',
            iai: 2,
            hpe: 20,
            qty: 0
          },
          {
            date: '2020-09-14',
            iai: 1,
            hpe: 16,
            qty: NaN
          }
        ]
      },
      data5: {
        name: 'N9Z38AA',
        data: [
          {
            date: '2020-06-01',
            iai: 6,
            hpe: 13,
            qty: 14
          },
          {
            date: '2020-06-08',
            iai: 5,
            hpe: 13,
            qty: 18
          },
          {
            date: '2020-06-15',
            iai: 6,
            hpe: 13,
            qty: 10
          },
          {
            date: '2020-06-22',
            iai: 5,
            hpe: 15,
            qty: 20
          },
          {
            date: '2020-06-29',
            iai: 8,
            hpe: 13,
            qty: 0
          },
          {
            date: '2020-07-06',
            iai: 7,
            hpe: 16,
            qty: 4
          },
          {
            date: '2020-07-13',
            iai: 5,
            hpe: 16,
            qty: 18
          },
          {
            date: '2020-07-20',
            iai: 8,
            hpe: 16,
            qty: 8
          },
          {
            date: '2020-07-27',
            iai: 7,
            hpe: 15,
            qty: 2
          },
          {
            date: '2020-08-03',
            iai: 7,
            hpe: 12,
            qty: 16
          },
          {
            date: '2020-08-10',
            iai: 11,
            hpe: 7,
            qty: 16
          },
          {
            date: '2020-08-17',
            iai: 8,
            hpe: 7,
            qty: 8
          },
          {
            date: '2020-08-24',
            iai: 7,
            hpe: 7,
            qty: 208
          },
          {
            date: '2020-08-31',
            iai: 10,
            hpe: 7,
            qty: 38
          },
          {
            date: '2020-09-07',
            iai: 9,
            hpe: 7,
            qty: 4
          },
          {
            date: '2020-09-14',
            iai: 7,
            hpe: 7,
            qty: NaN
          }
        ]
      },
      data6: {
        name: 'P11908-001',
        data: [
          {
            date: '2020-06-01',
            iai: 137,
            hpe: 352,
            qty: 96
          },
          {
            date: '2020-06-08',
            iai: 126,
            hpe: 409,
            qty: 161
          },
          {
            date: '2020-06-15',
            iai: 109,
            hpe: 411,
            qty: 220
          },
          {
            date: '2020-06-22',
            iai: 88,
            hpe: 479,
            qty: 130
          },
          {
            date: '2020-06-29',
            iai: 50,
            hpe: 856,
            qty: 168
          },
          {
            date: '2020-07-06',
            iai: 85,
            hpe: 401,
            qty: 42
          },
          {
            date: '2020-07-13',
            iai: 62,
            hpe: 405,
            qty: 36
          },
          {
            date: '2020-07-20',
            iai: 259,
            hpe: 446,
            qty: 206
          },
          {
            date: '2020-07-27',
            iai: 98,
            hpe: 432,
            qty: 92
          },
          {
            date: '2020-08-03',
            iai: 89,
            hpe: 412,
            qty: 70
          },
          {
            date: '2020-08-10',
            iai: 349,
            hpe: 385,
            qty: 40
          },
          {
            date: '2020-08-17',
            iai: 242,
            hpe: 738,
            qty: 42
          },
          {
            date: '2020-08-24',
            iai: 229,
            hpe: 722,
            qty: 106
          },
          {
            date: '2020-08-31',
            iai: 142,
            hpe: 310,
            qty: 64
          },
          {
            date: '2020-09-07',
            iai: 142,
            hpe: 429,
            qty: 30
          },
          {
            date: '2020-09-14',
            iai: 190,
            hpe: 288,
            qty: NaN
          }
        ]
      }
    }
  },
  mounted () {
    this.data = this.data1.data
  },
  computed: {
    curName () {
      return this[`data${this.curIndex}`].name
    }
  },
  methods: {
    handleClick (index) {
      this.curIndex = index
      this.data = this[`data${index}`].data
    },
    getName (index) {
      return this[`data${index}`].name
    },
    exportExcel () {
    // this.data = this[`data${index}`].data
      let exportData = []
      for (let i = 1; i <= 6; i++) {
        exportData.push(this[`data${i}`])
      }
      if (exportData.length) {
        this.exportLoading = true
        const params = {
          title: ['Date', 'iAI prediction', 'HPE lead time prediction', 'Actual consumption'],
          key: ['date', 'iai', 'hpe', 'qty'],
          data: exportData,
          autoWidth: true,
          filename: 'Material prediction comparison'
        }
        excel.export_custom_to_excel(params)
        this.exportLoading = false
      } else {
        this.$Message.info('Table cannot be empty')
      }
    }
  }
}

</script>

<style lang="less">
.count-style{
  font-size: 50px;
}
</style>
