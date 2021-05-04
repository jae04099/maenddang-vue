<template>
  <div class="red lighten-3 pa-3">
    <h3>자세한 회원 정보를 확인합니다.</h3>
    <p>상세사항</p>
    <v-list dense>
        <v-list-item>
            <v-list-item-content>name:</v-list-item-content>
            <v-list-item-content class="align-end">
                {{name}}
            </v-list-item-content>
        </v-list-item>
        <v-list-item>
            <v-list-item-content>address:</v-list-item-content>
            <v-list-item-content class="align-end">
                {{address}}
            </v-list-item-content>
        </v-list-item>
        <v-list-item>
            <v-list-item-content>phone:</v-list-item-content>
            <v-list-item-content class="align-end">
                {{phone}}
            </v-list-item-content>
        </v-list-item>
        <v-list-item>
            <v-list-item-content>doggy:</v-list-item-content>
            <v-list-item-content class="align-end">
                {{hasDogKr}}
            </v-list-item-content>
        </v-list-item>
    </v-list>
  </div>
</template>
<script>
export default {
    props: ['name', 'address', 'phone','hasDog']
    ,
    computed: {
        hasDogKr(){
            return this.hasDog === true ? 'yes' : 'no'
        }
    },
}

// 부모 컴포넌트에서 이미 값이 상속 됐기 때문에 자식 프롭에서는 어떤 것도 넣으면 안됨. 오직, 타입만 지정해준다.
// required true를 했다면 반드시 부모가 보내야만 함. 그렇지 않으면 전달받지 않는다면 오류남.
</script>
