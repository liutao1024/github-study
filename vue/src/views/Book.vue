<template>
  <div>
    <table>
      <tr>
        <td>编号</td>
        <td>名称</td>
        <td>作者</td>
      </tr>
      <tr v-for="item in books" :key="item.id"><!-- 没有:key=会报红色错误,不过也能正常运行,vue2.2.++的-->
        <td>{{item.id}}</td>
        <td>{{item.name}}</td>
        <td>{{item.author}}</td>
      </tr>
    </table>
    {{msg}}
  </div>
</template>

<script>
export default {
  name: 'book',
  data() {
    return {
      msg: 'Hello Vue',
      books: [
        {
          id: '001',
          name: 'Java虚拟机实现与探索',
          author: '周作民'
        },
        {
          id: '002',
          name: '狂人日记',
          author: '鲁迅'
        },
        {
          id: '003',
          name: '从三味书屋到百草园',
          author: '周树人'
        }
      ]
    }
  },
  created() {
    const _this = this;
    axios.get('http://localhost:8181/book/findAll').then(function (rsp) {
      //this.tableData = rsp.
      console.log(rsp);
      _this.books = rsp.data;
    })
  }
}
</script>

<style scoped>

</style>
