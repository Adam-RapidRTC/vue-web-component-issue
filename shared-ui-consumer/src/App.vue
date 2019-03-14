<template>
  <div id="app">
    <shared-ui title="Test">
      <span :class="[$style.testClass]" slot="body-content">
        Here is some text
      </span>
    </shared-ui>
  </div>
</template>

<script lang="ts">
import 'vue'
import { Component, Vue } from 'vue-property-decorator';

@Component({ })
export default class App extends Vue {

}
</script>

<style lang="scss" module>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.testClass{
  color: red;
}
</style>
