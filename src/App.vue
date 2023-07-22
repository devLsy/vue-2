<template>
  <h2 class="menu">
    <a v-for="item in menus" :key="item.id" target="_blank">
      <span v-text="item"></span>
    </a>
  </h2>
  <!-- <table>  
    <thead>
      <th>제목</th>
      <th>이미지</th>
    </thead>
    <tbody>
      <tr v-for="item in data" :key="item.id">
        <td><span v-html="item.title"></span></td>
        <td><a target="_blank" :href="item.link"><img :src="item.image" class="thumnail"></a></td>
        <td v-text="item.subtitle" />
        <td v-text="item.pubDate" />
        <td v-text="item.director" />
        <td v-text="item.actor" />
        <td v-text="item.userRating" />
      </tr> 
    </tbody>
  </table> -->
  <ul>
    <li v-for="item in data" :key="item">
      <a target="_blank" :href="item.link"><img :src="item.image" class="thumnail"></a>
    </li>
  </ul>

</template>

<script>

import data from './assets/data.js';
data;

export default {
  name: 'App',
  data() {
    return {
      data: data,
      menus: ['전체', '음악', '믹스', '실시간', '시트콤', 
      '최근에 업로드된 동영상', '감상한 동영상', '새로운 맞춤 동영상'
      ],  
      products: ['thor', 'ironMan', 'doctor strange'],
    }
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
