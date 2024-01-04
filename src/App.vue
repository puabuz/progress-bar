<template>
  <div class="wrapper">
    <form v-if="!formDone" @submit.prevent="sendForm">
      <div @scroll="onScroll" class="sample">
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
      <div class="progress">
        <div class="progress_bar" :style="progressStyles"></div>
      </div>
      <div class="checkbox_wrapper">
        <template v-if="scrollDone">
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
        </template>
        <template v-if="flags.getSpam">
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
        </template>
      </div>
      <div v-if="scrollDone">
        <button :disabled="!formReady">Send Data</button>
      </div>
    </form>
    <div v-else>
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
          <tr v-if="flags.getSpam">
            <td>Spam type</td>
            <td>{{ spamType }}</td>
          </tr>
        </table>
      </div>
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
  computed: {
    progressStyles() {
      return {
        width: this.scrollValue * 100 + "%",
      };
    },
    scrollDone() {
      return this.scrollValue.toFixed(2) > 0.99;
    },
    formReady() {
      return this.scrollDone && this.flags.agree;
    },
  },
  methods: {
    onScroll(e) {
      let el = e.target;
      this.scrollValue = Math.max(
        this.scrollValue,
        el.scrollTop / (el.scrollHeight - el.clientHeight)
      );
      console.log(this.scrollDone);
    },
    sendForm() {
      if (this.formReady) {
        this.formDone = true; //запрос на сервер
      }
    },
  },
};
</script>

<style>
#app {
  box-sizing: content-box;
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
  overflow: auto;
  border: 1px solid gray;
}

.checkbox_wrapper {
  margin: 15px auto;
  width: 400px;
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

.progress {
  width: 400px;
  margin: 0 auto;
}

.progress_bar {
  height: 8px;
  background-color: cadetblue;
}
</style>
