<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button class="toggle-print" v-on:click="tooglePrint">Toggle</button>
    <section class="tabs-component-panel" v-bind:class="{ print: isPrint }">
      <p>Tab 1</p>
    </section>
    <section class="tabs-component-panel" v-bind:class="{ print: isPrint }">
      <p>Tab 2</p>
    </section>
    <section class="tabs-component-panel" v-bind:class="{ print: isPrint }">
      <p>Tab 3</p>
    </section>
    <section class="tabs-component-panel" v-bind:class="{ print: isPrint }">
      <p>Tab 4</p>
    </section>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function() {
    return {
      isPrint: false
    }
  },
  methods: {
    tooglePrint: function () {
      this.isPrint = !this.isPrint;
      if (this.isPrint) {
        this.$nextTick(() => {
          window.print();
        });
      }
      //alert('toggle');
    }
  }
}
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

section.tabs-component-panel {
  display: none;
  padding: 50px 20px;
  background: #eee;
}
section.tabs-component-panel:first-of-type {
  display: block;
  padding: 50px 20px;
  background: #eee;
}
section.tabs-component-panel.print {
  display: block;
}
.toggle-print {
  background: #42b983;
  color: #FFF;
  border: 0;
  border-radius: 3px;
  padding: 1em;
}
</style>
