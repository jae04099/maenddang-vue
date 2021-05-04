<template>
  <div class="yellow lighten-3 pa-3">
    <h3>회원 정보를 수정할 수 있습니다.</h3>
    <p>수정사항</p>
    <v-text-field label="이름" v-model="user.name"></v-text-field>
    <v-text-field label="주소" v-model="user.address"></v-text-field>
    <v-text-field label="전화번호" v-model="user.phone"></v-text-field>
    <v-radio-group v-model="user.hasDog">
      <v-radio label="has dog" :value="true"></v-radio>
      <v-radio label="no" :value="false"></v-radio>
    </v-radio-group>
    <v-btn @click="changeUser">수정 완료</v-btn>
  </div>
</template>

<script>
export default {
  props: ["name", "address", "phone", "hasDog"],
  data() {
    return {
      user: {},
    };
  },
  created() {
    this.user.name = this.name;
    this.user.address = this.address;
    this.user.phone = this.phone;
    this.user.hasDog = this.hasDog;
  },

  methods: {
      changeUser(){
          this.$emit('child', this.user)
      }
  }
};

// 받아온 props를 자식 컴포넌트 안에서 직접적으로 바꾸면 문제가 됨. 때문에, 자식에서 한번 가공하고 넣어주어야 함.
// 컴포넌트가 created 됐을 때, UserEdit 컴포넌트 내에 있는 user 객체에 재할당 시켜줌.
// 부모컴포넌트를 통해 자식컴포넌트로 props를 이용해 name이라는 값을 전달해줌. name을 자식컴포넌트 자체의 user에 넣었다. 그리고 user.name을 연결함.
// 때문에, 자식컴포넌트에 아무리 수정을 해도 부모값은 아니기 때문에 에러메세지가 뜨지 않음.
</script>
