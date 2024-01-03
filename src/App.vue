<template>
  <div class="wrapper">
    <form action="">
      <div class="sample">
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
        <p>Lorem ipsum dolor sit elit. Commodi, eligendi.</p>
      </div>
      <div class="checkbox_wrapper">
        <div>
          <label>
            <input type="checkbox" v-model="flags.agree" />
            Agree All
          </label>
        </div>
        <div>
          <label>
            <input type="checkbox" v-model="flags.getSpam" />
            Get Spam
          </label>
        </div>
        <div>
          <label>
            <input type="radio" v-model="spamType" value="email" />
            email
          </label>
        </div>
        <div>
          <label>
            <input type="radio" v-model="spamType" value="phone" />
            Phone
          </label>
        </div>
      </div>
      <button>Send Data</button>
    </form>
    <hr />
    <div>
      <table>
        <tr>
          <td>Agree All</td>
          <td>{{ flags.agree ? 1 : 0 }}</td>
        </tr>
        <tr>
          <td>Get Spam</td>
          <td>{{ flags.getSpam ? 1 : 0 }}</td>
        </tr>
        <tr>
          <td>Spam type</td>
          <td>{{ spamType }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      formDone: false,
      scrollValue: 0,
      flags: {
        agree: false,
        getSpam: false,
      },
      spamType: "",
    };
  },
  methods: {
    onScroll(e) {
      console.log(e);
    },
    sendForm() {
      console.log();
    },
  },
  // computed: {

  // }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.sample {
  margin: 0 auto;
  width: 400px;
  height: 350px;
  overflow-y: scroll;
  border: 1px solid gray;
}

.checkbox_wrapper {
  margin: 15px auto;
  width: 400px;
  border: 1px solid gray;
  text-align: start;
}

table {
  margin: 0 auto;
  border: 1px solid gray;
}

td {
  border: 1px solid gray;
  width: 200px;
}
</style>
