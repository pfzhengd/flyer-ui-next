<script>
import { h } from 'vue'
export default {
  name: 'FlyRow',
  props: {
    gutter: {
      type: Number,
      default: 0
    },
    type: {
      type: String,
      default: 'flex'
    },
    justifyContent: {
      type: String,
      default: 'stretch',
      validator (value) {
        return ['stretch', 'flex-start', 'flex-end', 'center', 'space-around', 'space-between'].indexOf(value) > -1
      }
    },
    alignItems: {
      type: String,
      default: 'stretch',
      validator (value) {
        return ['stretch', 'flex-start', 'flex-end', 'center'].indexOf(value) > -1
      }
    },
    tagName: {
      type: String,
      default: 'div'
    }
  },
  computed: {
    style () {
      return {
        'margin-left': this.gutter > 0 ? `-${this.gutter / 2 / 14}rem` : '',
        'margin-right': this.gutter > 0 ? `-${this.gutter / 2 / 14}rem` : '',
        'justify-content': this.justifyContent,
        'align-items': this.alignItems
      }
    }
  },
  render () {
    return h(this.tagName, {
      class: ['fly-row', this.type === 'flex' ? 'fly-row--flex' : ''],
      style: this.style
    }, this.$slots.default ? this.$slots.default() : [])
  }
}
</script>
<style lang="scss">
@import './index.scss';
</style>
