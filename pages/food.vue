<template>
  <div>
    <section class="hero is-link">
      <div class="hero-body">
        <p class="title">
          <i class="fas fa-glass-martini-alt" /> 맛집 리스트
        </p>
        <p class="subtitle">
         맛집을 평가해드립니다
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
          <th>이름</th>
          <th>content</th>
        </tr>
      </thead>
      <tbody>
        <template v-for="pos in tablefoodKeys.length">
          <tr :key="pos">
            <td>{{ pos }}</td>
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
    const foodlist = await axios.get('https://raw.githubusercontent.com/swmaestro/somat/gh-pages/somalife.json')
    alert(Object.keys(foodlist.data[0]))
    return {
      tablefood: foodlist.data,
      tablefoodkey: Object.keys(foodlist.data[0]
      )
    }
  }
}
</script>