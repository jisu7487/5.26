<template>
  <div>
    <section class="hero is-link">
      <div class="hero-body">
        <p class="title">
          <i class="fas fa-utensils"></i> 우리동네
          <i class="fas fa-utensils"></i> 맛집정보
        </p>
        <p class="subtile">
          맛집 list
        </p>
      </div>
    </section>
    <hr />
    <section class="columns">
      <div class="column">
        <table class="table is-striped is-hoverable is-fullwidth">
          <thead>
            <tr>
              <th>번호</th>
              <th>가게이름</th>
              <th>대표메뉴</th>
            </tr>
          </thead>
          <tbody>
            <template v-for="pos in tableResMenu.length">
              <tr :key="pos">
                <td>{{ pos }}</td>
                <td>{{ tableResMenu[pos - 1] }}</td>
                <td>{{ tableResName[pos - 1] }}</td>
              </tr>
            </template>
          </tbody>
        </table>
        <div class="content">
          <span class="tag is-danger">출처</span>
          <a href="https://github.com/sindresorhus/dog-names"
            >sindresorhus/dog-names</a
          >
        </div>
      </div>
      <div class="column">
        <table class="table is-striped is-hoverable is-fullwidth">
          <thead>
            <tr>
              <th>번호</th>
              <th>고양이 이름</th>
            </tr>
          </thead>
          <tbody>
            <template v-for="pos in tableCatNames.length">
              <tr :key="pos">
                <td>{{ pos }}</td>
                <td>{{ tableCatNames[pos - 1] }}</td>
              </tr>
            </template>
          </tbody>
        </table>
        <div class="content">
            <span class="tag is-danger">출처</span>
            <a href="https://github.com/sindresorhus/cat-names"
              >sindresorhus/cat-names</a
            >
          </div>
      </div>
    </section>
  </div>
</template>
<script>
import ResMenu from "~/assets/ResMenu.json";
import ResName from "~/assets/ResName.json";
import catNames from "~/assets/catNames.json";
export default {
  data() {
    return {
      tableResMenu: ResMenu.names,
      tableResName: ResName.names,
      tableCatNames: catNames.names
    };
  }
};
</script>
