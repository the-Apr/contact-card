<template>
<div class="liShadow justify-center p-10 mb-5">
  <section  class="text-center">
    <h2 class="text-2xl text-white idk bb mb-4 rounded-lg p-4">
      {{ name }} {{ isFavorite? '(Favorite)': ''}}
    </h2>
    <button class="bg-pink-500 py-2 px-3 rounded-2xl text-white cursor-pointer btnShadow mr-4" @click="toggleFavorite">toggle favorite</button>
    <button class="bg-pink-500 py-2 px-3 rounded-2xl text-white cursor-pointer btnShadow mr-4" 
    @click="toggleDetails"> {{detailsAreVisible? 'Hide' : 'Show'}} 
    Details</button>
    <button class="bg-pink-500 py-2 px-3 rounded-2xl text-white cursor-pointer btnShadow" 
    @click="$emit('delete',this.id)"> Delete</button>
    <ul v-if="detailsAreVisible" class="mb-5">
      <li class="liShadow p-4 my-4">
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li class="liShadow p-4 my-4">
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </section>
  </div>
</template>

<script>
export default {
  // props : ['name','phoneNumber','emailAddress','isFavorite'],
  props: {
    id:{
      type: String,
      required: true
    },
    name:{
      type: String,
      required: true
    },
    phoneNumber:{
      type: String,
      required: true
    },
    emailAddress:{
      type: String,
      required: true
    },
    isFavorite:{
      type: Boolean,
      required: false,
      default: '0',
      validator: function(value){
        return value ==='1' || value ==='0';
      }
    }
  },
  emits: ['toggle-Favorite'],
  // emits:{
  //   'toggle-Favorrite' : function(id){
  //     if(id){
  //       return true;
  //     }
  //     else{
  //       console.log('Id missing');
  //       return false;
  //     }
  //   }
  // },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite(){
      this.$emit('toggle-Favorite', this.id);
    },
  },
};
</script>