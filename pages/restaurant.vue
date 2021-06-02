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
              <th>가게위치</th>
            </tr>
          </thead>
          <tbody>
            <template v-for="pos in tableResMenu.length">
              <tr :key="pos">
                <td>{{ pos }}</td>
                <td>{{ tableResName[pos - 1] }}</td>
                <td>{{ tableResMenu[pos - 1] }}</td>
                <td>{{ tableResLocation[pos - 1] }}</td>
              </tr>
            </template>
          </tbody>
        </table>
        <div class="content">
          <span class="tag is-danger">출처</span>
          <a href="http://www.kimbab1009.com/"
            >김밥천국</a
          >
        </div>
      
      </div>
    </section>
  </div>
</template>
<script>
import ResName from "~/assets/ResName.json";
import ResMenu from "~/assets/ResMenu.json";
import ResLocation from "~/assets/ResLocation.json";
export default {
  data() {
    return {
      tableResName: ResName.names,
      tableResMenu: ResMenu.names,
      tableResLocation: ResLocation.names
    };
  }
};
</script>
