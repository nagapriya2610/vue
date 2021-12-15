<template>
	<div class="text-end mb-5">
		<a v-bind:href="'/create'" class="btn btn-primary">ADD</a>
	</div>
	<table class="table table-bordered">
		<thead>
			<tr>
			   <th>Id</th>
			   <th>Name</th>
			   <th>Email</th>
			   <th>Gender</th>
			   <th>Qualification</th>
		    </tr>
		</thead>
		<tbody>
			<tr v-for="row in data">
				<td>{{row.id}}</td>
				<td>{{row.name}}</td>
				<td>{{row.email}}</td>
				<td>{{row.gender}}</td>
				<td>{{row.qualification}}</td>
			</tr>
		</tbody>
	</table>
</template>

<script>
	export default{
		props:['data'],
	}
</script>