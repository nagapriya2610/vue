<template>
	<div class="text-end">
	<a v-bind:href="'/'" class="btn btn-primary" onclick="back()">Back</a>
   </div>
	<center>
		<div v-if="error" class="alert-danger">error</div>
		<div v-if="success" class="alert-success">success</div>
	<form class="col-5 shadow" @submit.prevent="submit">
		<br><br>
		<table cellpadding="10px" class="w-75 ms-4 me-4">
			<tr>
				<td>
					<label class="fw-bold">Name</label>
				</td>
			</tr>
			<tr>
				<td><div class="form-group@{{ errors.name ? ' has-error' : '' }}">
					<input type="text"  class="form-control" v-model="form.name" name="name">
					<form-error v-if="errors.name" :errors="errors">
                        @{{ errors.name }}
                    </form-error>
                  </div>
				</td>
			</tr>

			<tr>
				<td>
					<label class="fw-bold">Gender</label>
				</td>
			</tr>
			<tr>
				<td>
					<input type="radio"  class="form-check-input" v-model="form.gender" value="Male">&nbsp;&nbsp;Male&nbsp;&nbsp;
					<input type="radio"  class="form-check-input" v-model="form.gender" value="Female">&nbsp;&nbsp;Female&nbsp;&nbsp;
				</td>
			</tr>
			<tr>
				<td>
					<label class="fw-bold">Qualification</label>
				</td>
			</tr>
			<tr>
				<td>
					<select class="form-select" v-model="form.qualification">
						<option value="Diploma">Diploma</option>
						<option value="Bachelor Degree">Bachelor Degree</option>
						<option value="Master Degree">Master Degree</option>
					</select>
				</td>
			</tr>

			<tr>
				<td>
					<label class="fw-bold">Email</label>
				</td>
			</tr>

			<tr>
				<td>
					<input type="text" class="form-control" v-model="form.email">
				</td>
			</tr>

			<tr>
				<td>
					<input type="submit" value="Save Data" class="btn btn-primary w-100">
				</td>
			</tr>
		</table>
		<br><br>
	</form>
</center>
</template>

<script>

	import axios from 'axios'
	import FormError from './FormError.vue'
	export default{
		data:()=>({
			errors:[],
			form:{
				name:null,
				gender:null,
				email:null,
				qualification:null
			},
		}),
		methods:{
			submit(){
		       axios.post("/",this.form).then(res=>{
               this.onSuccess(res.data)
               alert('Employee Added')
               this.$set('errors', '');
            }).catch(error=>{
            	
            }),
            function(response){
		       	this.$set('errors',response.data)
		     }
			},

			back() {
				//
			}
		},
	}
</script>