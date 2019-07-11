<template>
  <section class="container">
    <h1>{{title}}</h1>
    <p>{{message}}</p>
    <table>
      <tr>
        <th>Email</th>
        <td>
          <input v-model="email" />
        </td>
        <td>
          <button @click="delData">Click</button>
        </td>
      </tr>
    </table>
    <hr />
    <ul v-for="(data, key) in json_data">
      <li>
        <strong>{{key}}</strong>
        <br />
        {{data}}
      </li>
    </ul>
  </section>
</template>


<script>
const axios = require("axios");

let url = "https://boobypenguin-vuejs-nuxtjs-app.firebaseio.com/person"; //★

export default {
  data: function() {
    return {
      title: "Axios",
      email: "",
      message: "axios sample.",
      json_data: {}
    };
  },
  methods: {
    delData: function() {
      let del_url = url + "/" + this.email + ".json";

      axios.delete(del_url).then(re => {
        this.message = this.email + "を削除しました。";
        this.email = "";
        this.getData();
      });
    },
    getData: function() {
      axios
        .get(url + ".json")
        .then(res => {
          this.json_data = res.data;
        })
        .catch(error => {
          this.message = "ERROR!";
          this.json_data = {};
        });
    }
  },
  created: function() {
    this.getData();
  }
};
</script>


<style>
ul {
  margin: 0px 10px;
  background-color: aliceblue;
}
li {
  padding: 10px;
  font-size: 16pt;
}
input {
  font-size: 14pt;
}
button {
  font-size: 14pt;
}
tr th {
  width: 150px;
  background-color: darkblue;
  color: white;
  font-size: 16pt;
}
tr td {
  padding: 5px 10px;
  background-color: #eef;
  font-size: 14pt;
}
.container {
  padding: 5px 10px;
}
h1 {
  font-size: 60pt;
  color: #345980;
}
p {
  padding-top: 5px;
  font-size: 20pt;
}
div {
  font-size: 14pt;
}
pre {
  padding: 10px;
  font-size: 18pt;
  background-color: #efefef;
  white-space: pre-wrap;
}
hr {
  margin: 10px 0px;
}
</style>
