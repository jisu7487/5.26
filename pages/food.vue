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

			</table>
			<div class="content">
				<a
					class="button is-primary is-small"
					href="https://raw.githubusercontent.com/terrenjpeterson/caloriecounter/master/src/data/foods.json"
					>List all foodList</a
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
			const foodList = await axios.get('https://raw.githubusercontent.com/terrenjpeterson/caloriecounter/master/src/data/foods.json');
			//alert(Object.keys(foodList));
			return {
				tablefoodList: foodList.data.message,
				tablefoodKeys: Object.keys(foodList.data.message),
			};
		},
	};
</script>
