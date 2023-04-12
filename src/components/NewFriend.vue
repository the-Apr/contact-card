<template>
	<form @submit.prevent="submitData" class="liShadow p-10 mb-5 text-center my-4">
		<div class="m-4 ">
			<label for="" class="forLabels">Name</label>
      <input type="text" class="p-1 border" v-model="enteredName"/>
		</div>
		<div class="m-4">
			<label for="" class="forLabels">Phone</label>
      <input type="tel" class="p-1 border" v-model="enteredPhone"/>
		</div>
		<div class="m-4">
			<label for="" class="forLabels">E-mail</label>
      <input type="email" class="p-1 border" v-model="enteredEmail"/>
		</div>
		<div class="text-center">
			<button class="bg-pink-500 py-2 px-3 rounded-2xl text-white cursor-pointer btnShadow">
				Add Contact</button>
		</div>
	</form>
	
</template>

<script>
export default {
	emits : ['add-contact'],
	data(){
		return{
			enteredName: '',
			enteredPhone: '',
			enteredEmail: '',
		};
	},
	methods :{
		submitData(){
			this.$emit(
				'add-contact',
				this.enteredName,
				this.enteredPhone,
				this.enteredEmail
			);
		}
	}
};
</script>