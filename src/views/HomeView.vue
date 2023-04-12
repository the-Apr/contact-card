<template>
  <section class="container">
    <div class="max-w-xl rounded-lg  liShadow">
     <h2 class="my-8 p-4 idk text-white text-center text-3xl ">Friends</h2>
    </div>
    <ul>
      <new-friend @add-contact="addContact"></new-friend>
      <friend 
      v-for="friend in friends"
        :key='friend.id'
        :id= 'friend.id'
        :name= 'friend.name'
        :email-address= 'friend.email'
        :phone-number= 'friend.number'
        :isFavorite = 'friend.isFavorite'
        @toggle-Favorite= 'toggleFavoriteStatus'
        @delete= 'deleteFriend'
      ></friend>
    </ul>
  </section>
</template>

<script>
// @ is an alias to /src
import Friend from '@/components/Friend.vue'
import NewFriend from '@/components/NewFriend'
export default {
  name: 'HomeView',
  components: {
    Friend,
    NewFriend
  },
  data(){
    return{
      friends: [
        {
          id: "manuel",
          name: "John Lorenz",
          phone: "0123 45678 90",
          email: "manuel@localhost.com",
          isFavorite: true
        },
        {
          id: "julie",
          name: "Julie Jones",
          phone: "0987 654421 21",
          email: "julie@localhost.com",
          isFavorite: false
        },
      ],
    }
  },
  methods:{
    toggleFavoriteStatus(friendId){
      const identifiedFriend= this.friends.find(friend => friend.id === friendId);
      identifiedFriend.isFavorite = !identifiedFriend.isFavorite;
    },
    addContact(name,phone,email){
      const newFriendContact ={
        id: newDate.toISOString(),
        name: name,
        phone: phone,
        email: email,
        isFavorite: false,
      };
      this.friends.push(newFriendContact);
    },
    deleteFriend(friendId){
      this.friends= this.friends.filter((friend) => friend.id !== friendId)
    }
  },
};
</script>
