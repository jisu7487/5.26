<template>
	<div>
		<section class="hero is-warning">
			<div class="hero-body">
				<p class="title"><i class="fas fa-utensils"></i>  맛집 추천</p>
				<p class="subtile">
					다양한 맛집을 평가해 드림
				</p>
			</div>
		</section>
		<hr />
		<section class="columns"></section>
		<div class="column">
			<table class="table">
				<thead>
					<th>번호</th>
					<th>이름</th>
					<th>평가</th>
				</thead>
				<tbody>
					<template v-for="pos in tablefoodKeys.length">
						<tr :key="pos">
							<td>{{ pos }}</td>
							<td>{{ tablefoodKeys[pos - 1] }}</td>
							<td>
								<span
									class="tag is-black"
									v-if="
										((ar = tablefoodBreeds[tablefoodKeys[pos - 1]]),
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
				<a
					class="button is-primary is-small"
					href="https://raw.githubusercontent.com/terrenjpeterson/caloriecounter/master/src/data/foods.json"
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
			const foodBreeds = await axios.get('https://raw.githubusercontent.com/terrenjpeterson/caloriecounter/master/src/data/foods.json');
			//alert(Object.keys(foodBreeds));
			return {
				tablefoodBreeds: foodBreeds.data.message,
				tablefoodKeys: Object.keys(foodBreeds.data.message),
			};
		},
	};
</script>
