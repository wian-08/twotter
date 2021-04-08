<template>
    <div class="user-proflile">
        <div class="user-profile_user-panel">
            <h1 class="user-profile_userName">@{{userName}}</h1>
            <div class="user-profile_admin-badge" v-if= "user.isAdmin">
                Admin
            </div>
            <div class="user-profile_admin-badge" v-else>
                User
            </div>
            <div class="user-profile_follower-count">
                <strong>Follower: </strong> {{ followers }}
                 @ {{ user.userName }} - {{fullName}}
                     <button @click="followUser">
                          Follow
                     </button>
            </div>
        </div>
        <div class="user-profile_twoots-wrapper">
            <div>
        </div>
        </div>

    </div>
</template>

<script>
export default {
    name: "UserProfile",
    data() {
        return {
            followers: 0,
      user: {
        id:1,
        userName: 'Wian_D',
        firstName: 'Wian',
        lastName: 'Diedericks',
        email: 'diederickswian08@gamil.com',
        isAdmin: true,
        twoots: [
            {id: 1, content: 'I love Twotter' },
            {id: 2, content: 'Twotter is cool'},
        ]
        }
    }
},
  watch: {
    followers (newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.userName} has gained a follower!`)
      }

    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}` 
    }
  },
  methods: {
    followUser() {
      this.followers++
    }
  
  },
  mounted() {
    this.followUser();
  }
}

</script>

<style>
.user-profile {
    display: grid;
    grid-template-columns: 1fr 3fr;
    width: 100px;
    padding: 50px 5%;
}
.user-profile_user-panel {
    display: flex;
    flex-direction: column;
    margin-right: 50px;
    padding: 20px;
    background-color: aliceblue;
    border-radius: 5px;
    border: 1px solid #dfe3e8;
}
h1 {
    margin: 0;
}
.user-profile_admin-badge {
    background: purple;
    color: white;
    border-radius: 5px;
    margin-right: auto;
    font-weight: bold;
}
</style>