<template>
  <div class="evil-ad">
    <div class="ad-box">
      <div class="ad-close" ref="button" @click="onClick">X</div>
      <div class="ad-content" ref="content"><slot></slot></div>
    </div>
  </div>
</template>

<script>
const rand = () => Math.random() > 0.5

export default {
  name: 'EvilAd',
  data: () => ({ a: false, b: false }),

  mounted () {
    this.move()
    document.addEventListener('mousemove', e => this.onMouseMove(e))
  },

  computed: {
    button () {
      return this.$refs.button
    },

    content () {
      return this.$refs.content
    }
  },

  methods: {
    getLength (e) {
      const r = this.$refs.button.getBoundingClientRect()
      const x = r.left + this.$refs.button.offsetWidth / 2
      const y = r.top + this.$refs.button.offsetHeight / 2

      return Math.hypot(e.clientX - x, e.clientY - y)
    },

    onMouseMove (e) {
      while (this.getLength(e) < this.button.offsetWidth * 2) this.move()
    },

    move () {
      const a = rand()
      const b = rand()
      if (a === this.a && b === this.b) return

      if (a) {
        const oy = `-${this.button.offsetHeight}px`
        const mx = this.content.offsetWidth - this.button.offsetWidth

        this.button.style.right = ''
        this.button.style.left = `${Math.random() * mx | 0}px`

        if (b) {
          this.button.style.top = oy
          this.button.style.bottom = ''
        } else {
          this.button.style.top = ''
          this.button.style.bottom = oy
        }
      } else {
        const ox = `-${this.button.offsetWidth}px`
        const my = this.content.offsetHeight - this.button.offsetHeight

        this.button.style.bottom = ''
        this.button.style.top = `${Math.random() * my | 0}px`

        if (b) {
          this.button.style.left = ox
          this.button.style.right = ''
        } else {
          this.button.style.left = ''
          this.button.style.right = ox
        }
      }

      this.a = a
      this.b = b
    },

    onClick () {
      alert('wow you really clicked!')
    }
  }
}
</script>

<style scoped>
.evil-ad .ad-box {
  position: relative;
}

.evil-ad .ad-close {
  font-size: 16px;
  position: absolute;

  width: 24px;
  height: 24px;
  line-height: 24px;
  text-align: center;

  color: white;
  font-weight: bold;
  background-color: red;
}

.evil-ad .ad-content {
  min-width: 100px;
  min-height: 100px;

  box-sizing: content-box;
  border: 1px solid black;
}
</style>
