<template>
  <h2 class="menu">
    <a v-for="item in menus" :key="item.id" target="_blank">
      <span v-text="item"></span>
    </a>
  </h2>
  <table>  
    <thead>
      <th>번호</th>
      <th>제목</th>
      <th>내용</th>
      <th>작성자</th>
      <th>등록일</th>
    </thead>    
    <tbody v-if="result.length > 0">
      <tr v-for="item in result" :key="item.no">
        <td>{{ item.no }}</td>
        <td>{{ item.title }}</td>
        <td>{{ item.content }}</td>
        <td>{{ item.userId }}</td>
        <td>{{ item.regDate }}</td>
      </tr>   
    </tbody>
    <tbody v-else>
      <tr>
        <td colspan="6"><strong>데이터가 없습니다.</strong></td>
      </tr>
    </tbody>
  </table>

  <div>
  <!-- <button @click="getUsers">조회</button> -->
  </div>

</template>

<script>

import data from './assets/data.js';
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      data: data,
      result: [],
    }
  },
  mounted: function() {
      // axios.get ('http://localhost:9000/api/user/addressbook')
      axios.get ('http://localhost:9090/api/board')
        .then(response => { 
          this.result = response.data.list;
        console.log(response.data.list);
      })    
        .catch(error => { 
        console.log(error);
      })
    console.log("page load");
  },    
  methods: {
  },
  components: {
    
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a, span {
  color: white;
  padding: 10px;
}

.menu span {
  color: white;
}

.img {
  width: 100%;
  margin-top: 40px;
}

img.thumnail {
  width: 325px; height: 98px;
}

ul li {
  list-style-type: none;
  float: left;
  margin-right: 20px;
}

</style>
