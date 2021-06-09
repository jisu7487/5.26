<template>
  <div>
    <section class="hero is-link">
      <div class="hero-body">
        <p class="title">
          <i class="fas fa-glass-martini-alt" /> 지역별 맛집
        </p>
        <p class="subtitle">
          맛집을 추천해 드립니다
        </p>
      </div>
    </section>

    <hr>
    <section class="columns" />
    <div class="colums" />
    <table class="table">
      <thead>
        <tr>
          <th>번호</th>
          <th>종류</th>
          <th>맛집</th>
        </tr>
      </thead>
      <tbody>
        <template v-for="pos in tablefood.length">
          <tr :key="pos">
            <td>{{ pos }}</td>
            <td>{{ tablefood[pos - 1].family }}</td>
            <td>{{ tablefood[pos - 1].food }}</td>
          </tr>
        </template>
      </tbody>
    </table>
    <div class="colums" />
  </div>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData () {
    const foodd = await axios.get('https://www.daegufood.go.kr/kor/xml/tastyfood.html?f_taste=1')
    alert(Object.keys(foodd.data[0]))
    return {
      tablefood: foodd.data,
      tablefoodkey: Object.keys(foodd.data[0]
      )
    }
  }
}
</script>