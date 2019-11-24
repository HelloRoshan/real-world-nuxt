<template>
  <div>
    <header>
      <h1>Tic Tac Toe (implementation in Vue)</h1>
      <p class="playins-info">
        <b>{{ activeSymbol }}</b>
        's Turn
      </p>
    </header>
    <div class="max-width-300">
      <div v-for="m in 3" :key="m + 'row'" class="columns">
        <div
          v-for="n in 3"
          @click.once="toggleSymbol($event, m, n)"
          :key="n + 'col'"
          :class="{ disabled: gameEnd }"
          class="t3-box column is-one-third"
        ></div>
      </div>
    </div>
    <h2 v-if="gameEnd" class="winner-text">{{ winner }} Wins</h2>
    <!-- TODO: Add restart game -->
    <!-- TODO: Add indivisual wins -->
    <!-- TODO: Add Custom Name -->
    <!-- TODO: Add custom X and O Choose option -->
    <!-- TODO: Case for Draw -->
  </div>
</template>
<script>
export default {
  name: 'VueT3',
  data() {
    return {
      activeSymbol: 'O',
      gameEnd: false,
      winner: null,
      symbols: ['O', 'X'],
      OData: [],
      XData: [],
      winCases: [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9],
        [1, 4, 7],
        [2, 5, 8],
        [3, 6, 9],
        [1, 5, 9],
        [3, 5, 7]
      ]
    }
  },
  methods: {
    toggleSymbol(el, row, col) {
      if (this.activeSymbol === 'O') {
        this.OData.push(3 * (row - 1) + col)
        if (this.OData.length >= 3) {
          this.winCases.forEach((w) => {
            let count = 0
            this.OData.forEach((o) => {
              if (w.includes(o)) {
                count++
              }
            })
            console.log('o' + count)
            if (count === 3) {
              this.winner = this.activeSymbol
              this.gameEnd = true
              return true
            } else {
              count = 0
            }
          })
        }
      } else {
        this.XData.push(3 * (row - 1) + col)
        if (this.XData.length >= 3) {
          this.winCases.forEach((w) => {
            let count = 0
            this.XData.forEach((x) => {
              if (w.includes(x)) {
                count++
              }
            })
            console.log('x' + count)
            if (count === 3) {
              this.winner = this.activeSymbol
              this.gameEnd = true
              return true
            } else {
              count = 0
            }
          })
        }
      }
      el.target.innerHTML = this.activeSymbol
      this.activeSymbol = this.symbols.filter((s) => s !== this.activeSymbol)[0]
    }
  }
}
</script>
<style scoped>
header {
  margin: 1rem 0;
  text-align: center;
}
.playins-info {
  font-size: 1.3rem;
  font-family: Helvetica, sans-serif;
}
.t3-box {
  border: 1px solid #aaa;
  border-radius: 8px;
  font-size: 3.5rem;
  font-weight: bolder;
  font-family: Helvetica, sans-serif;
  height: 100px;
  text-align: center;
}
.disabled {
  pointer-events: none;
}
.max-width-300 {
  max-width: 300px;
  margin: 2rem auto;
  width: 100%;
}
.winner-text {
  color: green;
  font-size: 3rem;
  font-family: Helvetica, sans-serif;
  text-align: center;
  font-weight: bolder;
}
</style>
