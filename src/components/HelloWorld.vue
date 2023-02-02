<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <t-table
      :data="dataSource"
      :columns="columns"
      rowKey="index"
      :table-layout="tableLayout"
      bordered
    ></t-table>
  </div>
</template>

<script>
const data = []
for (let i = 0; i < 5; i++) {
  data.push({
    index: i + 1,
    applicant: ['贾明', '张三', '王芳'][i % 3],
    status: i % 3,
    channel: ['电子签署', '纸质签署', '纸质签署'][i % 3],
    detail: {
      email: ['w.cezkdudy@lhll.au', 'r.nmgw@peurezgn.sl', 'p.cumx@rampblpa.ru'][i % 3]
    },
    matters: ['宣传物料制作费用', 'algolia 服务报销', '相关周边制作费', '激励奖品快递费'][i % 4],
    time: [2, 3, 1, 4][i % 4],
    createTime: ['2022-01-01', '2022-02-01', '2022-03-01', '2022-04-01', '2022-05-01'][i % 4]
  })
}
const tableOperationColumn = {
  colKey: 'rowOperationButton',
  title: '操作列',
  cell: 'rowOperationButton',
  fixed: 'right',
  align: 'center',
  width: 120
}

const SingleColumn = {
  colKey: 'row-select',
  type: 'single',
  title: '单选',
  className: 'demo-single-select-cell',
  checkProps: { allowUncheck: true },
  width: 94,
  dataType: 'string',
  fixed: 'left',
  align: 'left'
}

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      tableLayout: 'fixed',
      dataSource: data,
      columns: [
        {
          colKey: 'applicant',
          title: '申请人',
          width: 100
        },
        {
          colKey: 'status',
          title: '审批状态',
          width: 120
        },
        { colKey: 'detail.email', title: '邮箱地址', width: 180 },
        { colKey: 'matters', title: '申请事项', width: 200 },
        {
          colKey: 'createTime',
          title: '申请日期',
          width: 120,
          fixed: this.rightFixedColumn >= 2 ? 'right' : undefined
        }
      ]
    }
  },
  mounted () {
    setTimeout(() => {
      this.columns = [SingleColumn, ...this.columns]
    })
    setTimeout(() => {
      this.columns = [...this.columns, tableOperationColumn]
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
