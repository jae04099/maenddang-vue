<template>
  <div class="blue lighten-3 pa-3">
    <h1>User component</h1>
    <p>name: vuejs</p>
    <hr />
    <v-layout row wrap>
      <v-flex xs12 sm6>
        <UserDetail
          :name="name"
          :address="address"
          :phone="phone"
          :hasDog="hasDog"
        ></UserDetail>
      </v-flex>
      <v-flex xs12 sm6>
        <UserEdit
          :name="name"
          :address="address"
          :phone="phone"
          :hasDog="hasDog"
          @child="parents"
        ></UserEdit>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import UserDetail from "./UserDetail.vue";
import UserEdit from "./UserEdit.vue";

export default {
  name: "User",
  components: {
    UserDetail,
    UserEdit,
  },
  data() {
    return {
      name: "vuejs",
      address: "seoul",
      phone: "1234-5678",
      hasDog: true,
    };
  },
  methods: {
      parents(user){
          this.name = user.name
          this.address = user.address
          this.phone = user.phone
          this.hasDog = user.hasDog
          console.log('parent got it')
      }
  }
};

// props는 자식컴포넌트에 적는 것. 보내고자 하는 데이터 바인딩을 부모에서 하는 것.
</script>

