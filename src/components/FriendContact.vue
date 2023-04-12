<template>
<div>
  <h2 class=""> {{ friends.name }} </h2>
  <button @click="toogleDetails"> Details</button>
  <ul v-if="toogleDetails">
    <li>
      <strong>Phone:</strong> {{friends.phone}}
    </li>
    <li>
      <strong>Email:</strong> {{friends.email}}
    </li>
  </ul>
  </div>
    
</template>

<script>
export default {
   data() {
    return{
      detailsAreVisible: false,
      friends: {
        id: 'john',
        name: 'John Legend',
        phone: '09053355519',
        email: 'p.o.adebayo218@gmail.com'
      },
    };
  },
  methods:{
    toogleDetails(){
      console.log('clicked')
      this.detailsAreVisible = !this.detailsAreVisible
    }
  }
};
</script>