<template>
  <div class="lucky-grid">
    <div class="content">
      <div :class="['content-item', active === index ? 'active' : '']" v-for="(item, index) in prizes" :key="index">
        <div class="content-item-box">
          <div class="top">
            <img :src="item.img">
          </div>
          <div class="bottom">
            {{ item.name }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
const defaultProps = {
  minCycle: 5 * 12, // 至少转动多少次
  speed: 200, // 初始转动速度
}
export default {
  name: 'LuckyGrid',
  props: {
    prizes: { type: Array, default: () => [] },
    minCycle: { type: Number, default: defaultProps.minCycle },
    speed: { type: Number, default: defaultProps.speed },
  },
  data () {
    return {
      active: 0, // 当前转动到哪个位置
      cycle: 0, // 转动多少次
      stopped: false, // 是否停止
      timer: null, // 定时器
      _speed: this.speed, // 初始转动速度
    }
  },
  methods: {
    start () {
      this.stopped = false
      this._speed = this.speed
      this.cycle = 0
      this.$emit('start')
      this.startRoll()
    },
    startRoll () {
      // 开始转动
      const count = this.prizes.length
      let index = this.active
      index += 1
      this.cycle++
      if (index > count - 1) {
        index = 0
      }
      this.active = index
      this.timer = setTimeout(() => {
        if (!this.stopped || this.cycle < this.minCycle) {
          if (this.cycle < 20) {
            // 小于10圈，则一直提速
            this._speed -= 8
          }
        } else {
          // 停止了，则减速
          this._speed += 20
        }
        this.startRoll()
        if (this._speed > 400) {
          clearInterval(this.timer)
          this.$emit('stop', this.active)
        }
      }, this._speed)
    },
    stop () {
      this.stopped = true
    }
  }
}
</script>
<style lang="less" scoped>
.lucky-grid {
  .content {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    // gap: 10px;
    &-item {
      background: #ffcc89;
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
      border-right: 2px solid #000000;
      border-top: 2px solid #000000;
      &:nth-of-type(3n + 1) {
        border-left: 2px solid #000000;
      }
      &:nth-last-child(1), &:nth-last-child(2), &:nth-last-child(3) {
        border-bottom: 2px solid #000000;
      }
      &.active {
        background-color: #ff9400;
        border: 2px solid #ff9400;
      }
      &-box {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
      }
      .top {
        max-width: 100%;
        max-height: 100%;
        img {
          width: 100%;
          height: 100%;
        }
      }
      .bottom {
        font-size: 20px;
        font-family: Skranji;
        color: #000000;
        line-height: 27px;
      }
    }
  }
}
</style>
