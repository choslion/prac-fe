<template>
  <div>
    <form @submit.prevent="submitForm">
      <div>
        <label for="userName">id:</label>
        <input id="userName" type="text" v-model="userName" />
      </div>
      <button type="submit">login</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
import { reactive } from "vue";
export default {
  setup() {
    const state = reactive({
      account: {
        mid: null,
        memberName: "",
      },
    });

    // http://localhost:3000/api/account로 하면 오류 발생
    axios.get("/api/account").then((res) => {
      state.account = res.data;
    });

    return { state };

    // import { ref } from "vue";
    // const userName = ref("");

    // const submitForm = function () {
    //   console.log(userName.value);
    //   const url = "http://localhost:3000";
    //   const data = {
    //     userName: userName.value,
    //   };

    //   axios
    //     .get("/#/", {
    //       params: { title: "vue.js는 조으다." },
    //       // headers: { "X-Api-Key": "my-api-key" },
    //       timeout: 1000, // 1초 이내에 응답이 없으면 에러 처리
    //     })
    //     .then((res) => {
    //       console.log(res.data);
    //     });

    //   axios
    //     .post(url, data)
    //     .then(function (response) {
    //       console.log(response.data.userName);
    //     })
    //     .catch(function (error) {
    //       console.log(error);
    //     });
    // };

    // return {
    //   userName,
    //   submitForm,
    // };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
