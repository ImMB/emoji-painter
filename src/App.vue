<template>
  <div id="app">
    <div id="canvas" :class="{'grid': showGrid}" :style="{'width': `${size}px`}">
      <div v-for="cell in canvas" :key="cell.id" :class="cell.bg"
      :style="{'height': `${size / rows}px`, 'width': `${size / rows}px`}" 
      @mousedown="color(cell.id, true)" @mouseover="color(cell.id, mouseClicked)"/>
    </div>
    <div id="options">
      <div class="color-picker f" @click="emoji = 'f'"></div>
      <div class="color-picker d" @click="emoji = 'd'"></div>
      <div class="color-picker z" @click="emoji = 'z'"></div>
      <div class="color-picker c" @click="emoji = 'c'"></div>
      <div class="color-picker e" @click="emoji = 'e'"></div>
      <div class="color-picker size" @click="brush = 5">5</div>
      <div class="color-picker size" @click="brush = 4">4</div>
      <div class="color-picker size" @click="brush = 3">3</div>
      <div class="color-picker size" @click="brush = 2">2</div>
      <div class="color-picker size" @click="brush = 1">1</div>
      <button @click="createCanvas">Reset</button>
      <button @click="generate">Generate</button>
      <button @click="showGrid = !showGrid">Toggle grid</button>
      <input type="range" min="3" max="36" v-model="rows" class="slider">
      <input type="range" min="100" max="800" v-model="size" class="slider">
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      canvas: [],
      rows: 36,
      size: 500,
      emoji: 'z',
      mouseClicked: false,
      brush: 1,
      code: '',
      showGrid: false
    }
  },
  computed: {
    cells() { return Number(this.rows) * Number(this.rows) }
  },
  methods: {
    createCanvas() {
      this.canvas = [];
      let i;
      for (i = 0; i < this.cells; i++) {
        this.canvas.push({
          id: i,
          bg: 'f',
          hl: false
        })
      }
    },
    color(id, canDraw) {
      if (!canDraw) { return };

      if (this.brush === 1) {
        this.canvas[id].bg = this.emoji; 
      } else if (this.brush === 2) { 
        if (this.canvas[id]) { this.canvas[id].bg = this.emoji; }
        if (this.canvas[(id + 1)]) { this.canvas[(id + 1)].bg = this.emoji; }
        if (this.canvas[(id - 1)]) { this.canvas[(id - 1)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows))]) { this.canvas[(id - Number(this.rows))].bg = this.emoji;
        if (this.canvas[(id + Number(this.rows))]) { this.canvas[(id + Number(this.rows))].bg = this.emoji; }
      } else if (this.brush === 3) { }
        if (this.canvas[id]) { this.canvas[id].bg = this.emoji; }
        if (this.canvas[(id + 1)]) { this.canvas[(id + 1)].bg = this.emoji; }
        if (this.canvas[(id - 1)]) { this.canvas[(id - 1)].bg = this.emoji; }
        if (this.canvas[(id + 2)]) { this.canvas[(id + 2)].bg = this.emoji; }
        if (this.canvas[(id - 2)]) { this.canvas[(id - 2)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows))]) { this.canvas[(id - Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows))]) { this.canvas[(id + Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) * 2)]) { this.canvas[(id - Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows) * 2)]) { this.canvas[(id + Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) - 1)]) { this.canvas[(id - Number(this.rows) - 1)].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows) - 1)]) { this.canvas[(id + Number(this.rows) - 1)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) + 1)]) { this.canvas[(id - Number(this.rows) + 1)].bg = this.emoji;
        if (this.canvas[(id + Number(this.rows) + 1)]) { this.canvas[(id + Number(this.rows) + 1)].bg = this.emoji; }
      } else if (this.brush === 4) { }
        if (this.canvas[id]) { this.canvas[id].bg = this.emoji; }
        if (this.canvas[(id + 1)]) { this.canvas[(id + 1)].bg = this.emoji; }
        if (this.canvas[(id - 1)]) { this.canvas[(id - 1)].bg = this.emoji; }
        if (this.canvas[(id + 2)]) { this.canvas[(id + 2)].bg = this.emoji; }
        if (this.canvas[(id - 2)]) { this.canvas[(id - 2)].bg = this.emoji; }
        if (this.canvas[(id + 3)]) { this.canvas[(id + 3)].bg = this.emoji; }
        if (this.canvas[(id - 3)]) { this.canvas[(id - 3)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows))]) { this.canvas[(id - Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows))]) { this.canvas[(id + Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) * 2)]) { this.canvas[(id - Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows) * 2)]) { this.canvas[(id + Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) * 3)]) { this.canvas[(id - Number(this.rows) * 3)].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows) * 3)]) { this.canvas[(id + Number(this.rows) * 3)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) - 1)]) { this.canvas[(id - Number(this.rows) - 1)].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows) - 1)]) { this.canvas[(id + Number(this.rows) - 1)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) + 1)]) { this.canvas[(id - Number(this.rows) + 1)].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows) + 1)]) { this.canvas[(id + Number(this.rows) + 1)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) + 2)]) { this.canvas[(id - Number(this.rows) + 2)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) - 2)]) { this.canvas[(id - Number(this.rows) - 2)].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows) + 2)]) { this.canvas[(id + Number(this.rows) + 2)].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows) - 2)]) { this.canvas[(id + Number(this.rows) - 2)].bg = this.emoji; }
        if (this.canvas[(id - 1 - Number(this.rows) * 2)]) { this.canvas[(id - 1 - Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id + 1 - Number(this.rows) * 2)]) { this.canvas[(id + 1 - Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id - 1 + Number(this.rows) * 2)]) { this.canvas[(id - 1 + Number(this.rows) * 2)].bg = this.emoji;
        if (this.canvas[(id + 1 + Number(this.rows) * 2)]) { this.canvas[(id + 1 + Number(this.rows) * 2)].bg = this.emoji; }
      } else { }
        if (this.canvas[id]) { this.canvas[id].bg = this.emoji; }
        if (this.canvas[(id + 1)]) { this.canvas[(id + 1)].bg = this.emoji; }
        if (this.canvas[(id - 1)]) { this.canvas[(id - 1)].bg = this.emoji; }
        if (this.canvas[(id + 2)]) { this.canvas[(id + 2)].bg = this.emoji; }
        if (this.canvas[(id - 2)]) { this.canvas[(id - 2)].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows))]) { this.canvas[(id - Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id - Number(this.rows) * 2)]) { this.canvas[(id - Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows))]) { this.canvas[(id + Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id + Number(this.rows) * 2)]) { this.canvas[(id + Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id + 1 - Number(this.rows))]) { this.canvas[(id + 1 - Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id - 1 - Number(this.rows))]) { this.canvas[(id - 1 - Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id + 2 - Number(this.rows))]) { this.canvas[(id + 2 - Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id - 2 - Number(this.rows))]) { this.canvas[(id - 2 - Number(this.rows))].bg = this.emoji;  }
        if (this.canvas[(id + 1 - Number(this.rows) * 2)]) { this.canvas[(id + 1 - Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id - 1 - Number(this.rows) * 2)]) { this.canvas[(id - 1 - Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id + 2 - Number(this.rows) * 2)]) { this.canvas[(id + 2 - Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id - 2 - Number(this.rows) * 2)]) { this.canvas[(id - 2 - Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id + 1 + Number(this.rows))]) { this.canvas[(id + 1 + Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id - 1 + Number(this.rows))]) { this.canvas[(id - 1 + Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id + 2 + Number(this.rows))]) { this.canvas[(id + 2 + Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id - 2 + Number(this.rows))]) { this.canvas[(id - 2 + Number(this.rows))].bg = this.emoji; }
        if (this.canvas[(id + 1 + Number(this.rows) * 2)]) { this.canvas[(id + 1 + Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id - 1 + Number(this.rows) * 2)]) { this.canvas[(id - 1 + Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id + 2 + Number(this.rows) * 2)]) { this.canvas[(id + 2 + Number(this.rows) * 2)].bg = this.emoji; }
        if (this.canvas[(id - 2 + Number(this.rows) * 2)]) { this.canvas[(id - 2 + Number(this.rows) * 2)].bg = this.emoji; }
      }
    },
    generate() {
      this.code = '';
      this.canvas.forEach(cell => {
        if (cell.id % Number(this.rows) === 0) { this.code += '\r\n' };
        this.code += `:${cell.bg}:`;
      });
      console.log(this.code);
    }
  },
  created() {
    this.createCanvas();
  },
  mounted() {
    document.addEventListener('mousedown', () => { this.mouseClicked = true; });
    document.addEventListener('mouseup', () => { this.mouseClicked = false; });
  },
  watch: {
    rows: function() {
      this.createCanvas()
    }
  }
}
</script>

<style lang="scss">
#canvas{
  margin: 100px auto;
  div{
    float: left;
    box-sizing: border-box;
  }
}

.grid{
  div{
    border: 1px solid rgba(0, 0, 0, 0.151);
    &:hover{
      background-color: black;
    }
  }
}

#options{
  clear: both;
}

.f{
  background-image: url('https://emoji.slack-edge.com/T028WT82J/f/7bfebd8ea15ce653.png');
  background-position: center;
  background-size: contain;
}
.d{
  background-image: url('https://emoji.slack-edge.com/T028WT82J/d/325ab8876f3ae31b.png');
  background-position: center;
  background-size: contain;
}
.z{
  background-image: url('https://emoji.slack-edge.com/T028WT82J/z/eb673abf910a9fdf.png');
  background-position: center;
  background-size: contain;
}
.c{
  background-image: url('https://emoji.slack-edge.com/T028WT82J/c/0349504d39dc25fe.png');
  background-position: center;
  background-size: contain;
}
.e{
  background-image: url('https://emoji.slack-edge.com/T028WT82J/e/aae158ad4bc8ad13.png');
  background-position: center;
  background-size: contain;
}

.color-picker{
  width: 30px;
  height: 30px;
}

.size{
  background-color: rgb(161, 211, 255);
  line-height: 30px;
  text-align: center;
}
</style>
