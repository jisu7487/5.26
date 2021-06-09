<template>
	<div>
		<section class="hero is-warning">
			<div class="hero-body">
				<p class="title"><i class="fas fa-dog"></i> 강아지 품종</p>
				<p class="subtile">
					다양한 강아지 품종을 함께 공부합시다.
				</p>
			</div>
		</section>
		<hr />
		<section class="columns"></section>
		<div class="column">
			<table class="table">
				<thead>
					<th>이름</th>
					<th>몰라</th>
					<th>태그</th>
				</thead>
				<tbody>
					<template v-for="pos in tableFoodKeys.length">
						<tr :key="pos">
							<td>{{ pos }}</td>
							<td>{{ tableFoodKeys[pos - 1] }}</td>
							<td>
								<span
									class="tag is-black"
									v-if="
										((ar = tablefood[tableFoodKeys[pos - 1]]),
										ar.length == 0)
									"
									>없음</span
								>
								<span v-else
									><template v-for="subbreed in ar"
										><span class="tag is-success" :key="subbreed">{{
											subbreed
										}}</span
										>&nbsp;</template
									>
								</span>
							</td>
						</tr>
					</template>
				</tbody>
			</table>
			<div class="content">
				<p class="tag is-danger">출처</p>
				<a href="http://data.jeonnam.go.kr/rest/namdofood/getNdfoodList">Dog CEO</a><br />
				<a
					class="button is-primary is-small"
					href="https://www.data.go.kr/catalog/15059097/openapi.json"
					>List all breeds</a
				>
			</div>
		</div>
		<div class="column"></div>
	</div>
</template>
<script>
	import axios from 'axios';
	export default {
		async asyncData() {
			const food = await axios.get('https://www.data.go.kr/catalog/15059097/openapi.json');
			//alert(Object.keys(food));
			return {
				tablefood: food.data.message,
				tableFoodKeys: Object.keys(food.data.message),
			};
		},
	};
</script>
