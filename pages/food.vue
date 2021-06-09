<template>
  <div>
    <section class="hero is-link">
      <div class="hero-body">
        <p class="title">
          <i class="fas fa-glass-martini-alt" /> 악기의
          <i class="fas fa-glass-cheers" /> 모든것 2
        </p>
        <p class="subtitle">
          악기를 골라주세요
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
        <template v-for="pos in tablefood.length">
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