<template>
  <div>
    <h1>todolist</h1>
    <table class='table'>
      <thead>
        <tr>
          <th>번호</th>
          <th>내용</th>
          <th>완 료 ~~여부</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for='(todo) in todoList' :key='todo.no'>
          <td>{{todo.no}}</td>
          <td>{{todo.contents}}</td>
          <td>{{todo.todoYn}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      todoList: []
    }
  },
  mounted () {
    this.getList()
  },
  methods: {
    async getList () {
      const response = await axios.get('/api/todoSelect')
      this.todoList = response.data
    }
  }
}
</script>

<style>

</style>
