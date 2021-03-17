<template>
  <div class="app" id="app">
    <h1>Progress meters in Vue - UI elements</h1>
    <p>Some neat progress meters for Vue</p>
    <ul>
        <Progress
          v-for="(bar, idx) in bars"
          :name="bar.cat"
          :value="bar.score"
          :color="bar.color"
          :key="'bar_' + idx"
          :max="6"
        />
    </ul>
  </div>
</template>

<script>
import Progress from './components/progress.vue'

export default {
  name: 'ProgressUI',
  data: function () {
      return {
          bars: [
              {
                  cat: "Overall rating",
                  score: 6,
                  color: '#1e81b0'
              },
              {
                  cat: "Quality",
                  score: 4,
                  color: '#eeeee4'
              },
              {
                  cat: "Usability of product",
                  score: 5,
                  color: '#e28743'
              },
              {
                  cat: "Customer Service",
                  score: 4,
                  color: '#eab676'
              },
              {
                  cat: "Delivery & Communication",
                  score: 4,
                  color: '#76b5c5'
              },
              {
                  cat: "Value",
                  score: 6,
                  color: '#1e81b0'
              }
          ]
      }
  },
  components: {
    Progress
  }
}
</script>

<style>
html, body, div, span, h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code, del, dfn, em, img, ins,
kbd, q, s, samp, small, strong, tt, var, dl, dt,
dd, ol, ul, li, fieldset, form, input, select, button, textarea, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, figcaption, figure,
footer, header, hgroup, main, menu, nav, section {
    margin: 0;
    padding: 0;
    border: 0;
    font-style: inherit;
    vertical-align: baseline;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #000;
    font-family: Helvetica, Arial, sans-serif;
    font-size: 16px;
    line-height: 1.25;
}

body, html {
    min-width: 320px;
    width: 100%;
    overflow-x: hidden;
}

button {
    border-radius: 0;
}

h1 {
   font-size: 2rem;
}

.app {
  text-align: center;
  color: #000;
  margin-top: 2.5rem;
  padding: 0 2.5rem;
}

ul {
  list-style: none;
}

</style>
