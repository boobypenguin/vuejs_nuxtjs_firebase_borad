<template>
  <section class="container">
    <h1>{{title}}</h1>
    <p>{{message}}</p>
    </div>
  </section>
</template>


<script>
import firebase from "firebase";

export default {
  data: function() {
    return {
      title: "Auth",
      message: "this is message."
    };
  },
  created: function() {
    var config = {
      // ●各自の設定を記述
      apiKey: "AIzaSyCSQGMXA1e4JB46Q4hxSWSsuR8okac12cM",
      authDomain: "boobypenguin-vuejs-nuxtjs-app.firebaseapp.com",
      databaseURL: "https://boobypenguin-vuejs-nuxtjs-app.firebaseio.com",
      projectId: "boobypenguin-vuejs-nuxtjs-app",
      storageBucket: "",
      messagingSenderId: "291797488686",
      appId: "1:291797488686:web:4db64352946c0a0c"
    };
    firebase.initializeApp(config);

    var provider = new firebase.auth.GoogleAuthProvider();
    var self = this;
    firebase
      .auth()
      .signInWithPopup(provider)
      .then(function(result) {
        self.message = result.user.displayName + ", " + result.user.email;
      });
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
