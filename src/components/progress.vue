<template>
  <li>
    <h2>{{ $attrs.name + ' - ' + prog + '%' }}</h2>
    <div class="prog" :class="{ 'visible': inView }" >
      <div :data-hover="$attrs.name + ' - ' + prog + '%'" :style="{ width: prog + '%', backgroundColor: color }"></div>
    </div>
  </li>
</template>

<script>
export default {
    data: function () {
        return {
            prog: 0,
            inView: false
        }
    },
    props: {
        color: String,
        value: Number,
        max: Number
    },
    methods: {
        inViewport() {
            let box = this.$el.getBoundingClientRect(),
                win = window,
                doc = document;
            return (
                box.top >= 0 &&
                box.left >= 0 &&
                box.bottom <= (win.innerHeight || doc.documentElement.clientHeight) &&
                box.right <= (win.innerWidth || doc.documentElement.clientWidth)
            );
        },
        isVisible() {
            this.inView = this.inViewport();
        }
    },
    mounted() {
        this.prog = Math.round(parseInt(this.$props.value) / this.$props.max * 100);
        this.isVisible();
        window.addEventListener('scroll', this.isVisible);
    }
}

</script>

<style scoped lang="scss">
li {
  position: relative;
}

h2 {
  text-align: left;
}

.prog {
  background: #D8D8D8;
  width: 100%;
  max-width: 26.875rem;
  overflow: hidden;
  margin: .5rem 0 1.25rem 0;

  &, div {
    border-radius: .313rem;
    height: 100%;
    min-height: 1.25rem;
  }

  div {
    display: block;
    transition: transform .4s ease;
    transform: translateX(-100%);
  }

  &.visible div {
    transform: translateX(0);
  }
}

</style>