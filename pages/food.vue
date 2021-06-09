<template>
	<div>
		<section class="hero is-warning">
			<div class="hero-body">
				<p class="title"><i class="fas fa-dog"></i>맛집을 추천해드립니다</p>
				<p class="subtile">
					애완동물의 상태를 간단하게 체크해봅시다.
				</p>
			</div>
		</section>
		<hr />
		<section class="columns"></section>
		<div class="column">
			<table class="table">
				<thead>
					<th>간단한 진단 내역</th>
					<th>애완동물</th>
                    <th>패턴 변화</th>
				</thead>
				<tbody>
					<template v-for="pos in tableStatusKey.length">
						<tr :key="pos">
							<td>{{ tableStatus[pos - 1]}}</td>
                            <td>{{ tableStatus2[pos - 1]}}</td>
                            <td>{{ tableStatus3[pos - 1]}}</td>						
						</tr>
					</template>
				</tbody>
			</table>
            <div class="content">
				<p class="tag is-danger">출처</p>
				<a href="https://github.com/jisu7487/5.26">MY GIT</a><br />
			</div>
		</div>
		<div class="column"></div>
	</div>
</template>
<script>
	import axios from 'axios';
	export default {
		async asyncData() {
			const petStat = await axios.get('https://raw.githubusercontent.com/jisu7487/5.26/master/food.json');
            //alert(Object.keys(petStat));
            console.log(Object.keys(petStat.data.message));
			return {
				tableStatus: petStat.data.message,
                tableStatusKey: Object.keys(petStat.data.message),
                tableStatus2: petStat.data.status,
                tableStatus3: petStat.data.status2
                
                
			};
		}
	};
</script>