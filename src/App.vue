<template>
  <div id="app">
    <div id="canvas" :class="{'grid': showGrid}" :style="{'width': `${size}px`}">
      <div v-for="cell in canvas" :key="cell.id" :class="cell.bg"
      :style="{'height': `${size / rows}px`, 'width': `${size / rows}px`}" 
      @mousedown="color(cell.id, true)" @mouseover="color(cell.id, mouseClicked)"/>
    </div>
    <div id='cssmenu'>
<ul>
   <li><a href='#'><span>Home</span></a></li>
   <li class='last'><a @click="generate" href='#'><span>Generuj</span></a></li>
   <li><a @click="createCanvas" href='#'><span>Resetuj rysunek</span></a></li>
     <li class='last'><a href='#'><span>Toggle grid</span></a></li>
   <li class='active has-sub'><a href='#'><span>Rozmiar pędzla</span></a>
      <ul>
         <li class='has'><a @click="brush = 1" href='#'><span>1</span></a>
          <li class='has'><a @click="brush = 2" href='#'><span>2</span></a>
           <li class='has'><a @click="brush = 3" href='#'><span>3</span></a>
            <li class='has'><a @click="brush = 4" href='#'><span>4</span></a>
             <li class='has'><a @click="brush = 5" href='#'><span>5</span></a>
         
         </li>
         
      </ul>
   </li>
   
 
</ul>
</div>

    <nav class="menu">
   <input type="checkbox" href="#" class="menu-open" name="menu-open" id="menu-open" />
   <label class="menu-open-button" for="menu-open">
    <span class="lines line-1"></span>
    <span class="lines line-2"></span>
    <span class="lines line-3"></span>
  </label>

   <a @click="emoji = 'f'" href="#" class="menu-item blue">  <img style="margin-top:20%;" src="https://emoji.slack-edge.com/T028WT82J/f/7bfebd8ea15ce653.png" alt="Smiley face" height="42" width="42"></a>
   <a @click="emoji = 'd'" href="#" class="menu-item green"> <i class="fa fa-coffee"></i> <img style="margin-top:20%;" src="https://emoji.slack-edge.com/T028WT82J/d/325ab8876f3ae31b.png" alt="Smiley face" height="42" width="42"></a></a> 
   <a @click="emoji = 'z'" href="#" class="menu-item red"> <i class="fa fa-heart"></i> <img style="margin-top:20%;" src="https://emoji.slack-edge.com/T028WT82J/z/eb673abf910a9fdf.png" alt="Smiley face" height="42" width="42"></a></a>
   <a @click="emoji = 'c'" ref="#" class="menu-item purple"> <i class="fa fa-microphone"></i> <img style="margin-top:20%;" src="https://emoji.slack-edge.com/T028WT82J/c/0349504d39dc25fe.png" alt="Smiley face" height="42" width="42"></a></a>
   <a @click="emoji = 'e'" href="#" class="menu-item orange"> <i class="fa fa-star"></i> <img style="margin-top:20%;" src="https://emoji.slack-edge.com/T028WT82J/e/aae158ad4bc8ad13.png" alt="Smiley face" height="42" width="42"></a></a>
   <a href="#" class="menu-item lightblue"> <i class="fa fa-diamond"></i> </a>
</nav>
    <div id="options">
      
     
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
body{
  background-color: #f5f5f5;
}

#canvas{
   margin-left: 31%;
   margin-top: 12%;
   position: fixed;
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
@media screen and (max-width: 700px) {
   body {
      padding: 170px 0 0 0;
      width: 100%
   }
}

a {
   color: inherit;
}

.menu-item,
.menu-open-button {
   background: #C06C84;
   border-radius: 100%;
   width: 80px;
   height: 80px;
   margin-left: -40px;
   position: absolute;
   color: #FFFFFF;
   text-align: center;
   line-height: 80px;
   -webkit-transform: translate3d(0, 0, 0);
   transform: translate3d(0, 0, 0);
   -webkit-transition: -webkit-transform ease-out 200ms;
   transition: -webkit-transform ease-out 200ms;
   transition: transform ease-out 200ms;
   transition: transform ease-out 200ms, -webkit-transform ease-out 200ms;
}

.menu-open {
   display: none;
}

.lines {
   width: 25px;
   height: 3px;
   background: #f5f5f5;
   display: block;
   position: absolute;
   top: 50%;
   left: 50%;
   margin-left: -12.5px;
   margin-top: -1.5px;
   -webkit-transition: -webkit-transform 200ms;
   transition: -webkit-transform 200ms;
   transition: transform 200ms;
   transition: transform 200ms, -webkit-transform 200ms;
}

.line-1 {
   -webkit-transform: translate3d(0, -8px, 0);
   transform: translate3d(0, -8px, 0);
}

.line-2 {
   -webkit-transform: translate3d(0, 0, 0);
   transform: translate3d(0, 0, 0);
}

.line-3 {
   -webkit-transform: translate3d(0, 8px, 0);
   transform: translate3d(0, 8px, 0);
}

.menu-open:checked + .menu-open-button .line-1 {
   -webkit-transform: translate3d(0, 0, 0) rotate(45deg);
   transform: translate3d(0, 0, 0) rotate(45deg);
}

.menu-open:checked + .menu-open-button .line-2 {
   -webkit-transform: translate3d(0, 0, 0) scale(0.1, 1);
   transform: translate3d(0, 0, 0) scale(0.1, 1);
}

.menu-open:checked + .menu-open-button .line-3 {
   -webkit-transform: translate3d(0, 0, 0) rotate(-45deg);
   transform: translate3d(0, 0, 0) rotate(-45deg);
}

.menu {
   margin-left: 80%;
   margin-top: 25%;
   position: fixed;
  //  margin-right: 290px;
  //  top: 0;
  //  bottom: 0;
  //  left: 0;
  //  right: 0;
   width: 80px;
   height: 80px;
   text-align: center;
   box-sizing: border-box;
   font-size: 26px;
}


/* .menu-item {
   transition: all 0.1s ease 0s;
} */

.menu-item:hover {
   background: #EEEEEE;
   color: #3290B1;
}

.menu-item:nth-child(3) {
   -webkit-transition-duration: 180ms;
   transition-duration: 180ms;
}

.menu-item:nth-child(4) {
   -webkit-transition-duration: 180ms;
   transition-duration: 180ms;
}

.menu-item:nth-child(5) {
   -webkit-transition-duration: 180ms;
   transition-duration: 180ms;
}

.menu-item:nth-child(6) {
   -webkit-transition-duration: 180ms;
   transition-duration: 180ms;
}

.menu-item:nth-child(7) {
   -webkit-transition-duration: 180ms;
   transition-duration: 180ms;
}

.menu-item:nth-child(8) {
   -webkit-transition-duration: 180ms;
   transition-duration: 180ms;
}

.menu-item:nth-child(9) {
   -webkit-transition-duration: 180ms;
   transition-duration: 180ms;
}

.menu-open-button {
   z-index: 2;
   -webkit-transition-timing-function: cubic-bezier(0.175, 0.885, 0.32, 1.275);
   transition-timing-function: cubic-bezier(0.175, 0.885, 0.32, 1.275);
   -webkit-transition-duration: 400ms;
   transition-duration: 400ms;
   -webkit-transform: scale(1.1, 1.1) translate3d(0, 0, 0);
   transform: scale(1.1, 1.1) translate3d(0, 0, 0);
   cursor: pointer;
   box-shadow: 3px 3px 0 0 rgba(0, 0, 0, 0.14);
}

.menu-open-button:hover {
   -webkit-transform: scale(1.2, 1.2) translate3d(0, 0, 0);
   transform: scale(1.2, 1.2) translate3d(0, 0, 0);
}

.menu-open:checked + .menu-open-button {
   -webkit-transition-timing-function: linear;
   transition-timing-function: linear;
   -webkit-transition-duration: 200ms;
   transition-duration: 200ms;
   -webkit-transform: scale(0.8, 0.8) translate3d(0, 0, 0);
   transform: scale(0.8, 0.8) translate3d(0, 0, 0);
}

.menu-open:checked ~ .menu-item {
   -webkit-transition-timing-function: cubic-bezier(0.935, 0, 0.34, 1.33);
   transition-timing-function: cubic-bezier(0.935, 0, 0.34, 1.33);
}

.menu-open:checked ~ .menu-item:nth-child(3) {
   transition-duration: 180ms;
   -webkit-transition-duration: 180ms;
   -webkit-transform: translate3d(0.08361px, -104.99997px, 0);
   transform: translate3d(0.08361px, -104.99997px, 0);
}

.menu-open:checked ~ .menu-item:nth-child(4) {
   transition-duration: 280ms;
   -webkit-transition-duration: 280ms;
   -webkit-transform: translate3d(90.9466px, -52.47586px, 0);
   transform: translate3d(90.9466px, -52.47586px, 0);
}

.menu-open:checked ~ .menu-item:nth-child(5) {
   transition-duration: 380ms;
   -webkit-transition-duration: 380ms;
   -webkit-transform: translate3d(90.9466px, 52.47586px, 0);
   transform: translate3d(90.9466px, 52.47586px, 0);
}

.menu-open:checked ~ .menu-item:nth-child(6) {
   transition-duration: 480ms;
   -webkit-transition-duration: 480ms;
   -webkit-transform: translate3d(0.08361px, 104.99997px, 0);
   transform: translate3d(0.08361px, 104.99997px, 0);
}

.menu-open:checked ~ .menu-item:nth-child(7) {
   transition-duration: 580ms;
   -webkit-transition-duration: 580ms;
   -webkit-transform: translate3d(-90.86291px, 52.62064px, 0);
   transform: translate3d(-90.86291px, 52.62064px, 0);
}

.menu-open:checked ~ .menu-item:nth-child(8) {
   transition-duration: 680ms;
   -webkit-transition-duration: 680ms;
   -webkit-transform: translate3d(-91.03006px, -52.33095px, 0);
   transform: translate3d(-91.03006px, -52.33095px, 0);
}

.menu-open:checked ~ .menu-item:nth-child(9) {
   transition-duration: 780ms;
   -webkit-transition-duration: 780ms;
   -webkit-transform: translate3d(-0.25084px, -104.9997px, 0);
   transform: translate3d(-0.25084px, -104.9997px, 0);
}

.blue {
   background-color: #669AE1;
   box-shadow: 3px 3px 0 0 rgba(0, 0, 0, 0.14);
   text-shadow: 1px 1px 0 rgba(0, 0, 0, 0.12);
}

.blue:hover {
   color: #669AE1;
   text-shadow: none;
}

.green {
   background-color: #70CC72;
   box-shadow: 3px 3px 0 0 rgba(0, 0, 0, 0.14);
   text-shadow: 1px 1px 0 rgba(0, 0, 0, 0.12);
}

.green:hover {
   color: #70CC72;
   text-shadow: none;
}

.red {
   background-color: #FE4365;
   box-shadow: 3px 3px 0 0 rgba(0, 0, 0, 0.14);
   text-shadow: 1px 1px 0 rgba(0, 0, 0, 0.12);
}

.red:hover {
   color: #FE4365;
   text-shadow: none;
}

.purple {
   background-color: #C49CDE;
   box-shadow: 3px 3px 0 0 rgba(0, 0, 0, 0.14);
   text-shadow: 1px 1px 0 rgba(0, 0, 0, 0.12);
}

.purple:hover {
   color: #C49CDE;
   text-shadow: none;
}

.orange {
   background-color: #FC913A;
   box-shadow: 3px 3px 0 0 rgba(0, 0, 0, 0.14);
   text-shadow: 1px 1px 0 rgba(0, 0, 0, 0.12);
}

.orange:hover {
   color: #FC913A;
   text-shadow: none;
}

.lightblue {
   background-color: #62C2E4;
   box-shadow: 3px 3px 0 0 rgba(0, 0, 0, 0.14);
   text-shadow: 1px 1px 0 rgba(0, 0, 0, 0.12);
}

.lightblue:hover {
   color: #62C2E4;
   text-shadow: none;
}

.credit {
   margin: 24px 20px 120px 0;
   text-align: right;
   color: #EEEEEE;
}

.credit a {
   padding: 8px 0;
   color: #C49CDE;
   text-decoration: none;
   transition: all 0.3s ease 0s;
}

.credit a:hover {
   text-decoration: underline;
}
#cssmenu {
   position: fixed;
  height: 44px;
  background: #355C7D;
  width: 99%;
}
#cssmenu ul {
  list-style: none;
  padding: 0;
  margin: 0;
  line-height: 1;
}
#cssmenu > ul {
  position: relative;
  display: block;
  background: #2b2f3a;
  width: 100%;
  z-index: 500;
}
#cssmenu:after,
#cssmenu > ul:after {
  content: ".";
  display: block;
  clear: both;
  visibility: hidden;
  line-height: 0;
  height: 0;
}
#cssmenu.align-right > ul > li {
  float: right;
}
#cssmenu.align-center ul {
  text-align: center;
}
#cssmenu.align-center ul ul {
  text-align: left;
}
#cssmenu > ul > li {
  display: inline-block;
  position: relative;
  margin: 0;
  padding: 0;
}
#cssmenu > ul > #menu-button {
  display: none;
}
#cssmenu ul li a {
  display: block;
  font-family: Helvetica, sans-serif;
  text-decoration: none;
}
#cssmenu > ul > li > a {
  font-size: 14px;
  font-weight: bold;
  padding: 15px 20px;
  color: #f5f5f5;
  text-transform: uppercase;
  -webkit-transition: color 0.25s ease-out;
  -moz-transition: color 0.25s ease-out;
  -ms-transition: color 0.25s ease-out;
  -o-transition: color 0.25s ease-out;
  transition: color 0.25s ease-out;
}
#cssmenu > ul > li.has-sub > a {
  padding-right: 32px;
}
#cssmenu > ul > li:hover > a {
  color: #f97c7c;
}
#cssmenu li.has-sub::after {
  display: block;
  content: "";
  position: absolute;
  width: 0;
  height: 0;
}
#cssmenu > ul > li.has-sub::after {
  right: 10px;
  top: 20px;
  border: 5px solid transparent;
  border-top-color: #7a8189;
}
#cssmenu > ul > li:hover::after {
  border-top-color: #ffffff;
}
#indicatorContainer {
  position: absolute;
  height: 12px;
  width: 100%;
  bottom: 0px;
  overflow: hidden;
  z-index: -1;
}
#pIndicator {
  position: absolute;
  height: 0;
  width: 100%;
  border: 12px solid transparent;
  border-top-color: #2b2f3a;
  z-index: -2;
  -webkit-transition: left .25s ease;
  -moz-transition: left .25s ease;
  -ms-transition: left .25s ease;
  -o-transition: left .25s ease;
  transition: left .25s ease;
}
#cIndicator {
  position: absolute;
  height: 0;
  width: 100%;
  border: 12px solid transparent;
  border-top-color: #2b2f3a;
  top: -12px;
  right: 100%;
  z-index: -2;
}
#cssmenu ul ul {
  position: absolute;
  left: -9999px;
  top: 70px;
  opacity: 0;
  -webkit-transition: opacity .3s ease, top .25s ease;
  -moz-transition: opacity .3s ease, top .25s ease;
  -ms-transition: opacity .3s ease, top .25s ease;
  -o-transition: opacity .3s ease, top .25s ease;
  transition: opacity .3s ease, top .25s ease;
  z-index: 1000;
}
#cssmenu ul ul ul {
  top: 37px;
  padding-left: 5px;
}
#cssmenu ul ul li {
  position: relative;
}
#cssmenu > ul > li:hover > ul {
  left: auto;
  top: 44px;
  opacity: 1;
}
#cssmenu.align-right > ul > li:hover > ul {
  left: auto;
  right: 0;
  opacity: 1;
}
#cssmenu ul ul li:hover > ul {
  left: 170px;
  top: 0;
  opacity: 1;
}
#cssmenu.align-right ul ul li:hover > ul {
  left: auto;
  right: 170px;
  top: 0;
  opacity: 1;
  padding-right: 5px;
}
#cssmenu ul ul li a {
  width: 130px;
  border-bottom: 1px solid #eeeeee;
  padding: 10px 20px;
  font-size: 12px;
  color: #9ea2a5;
  background: #ffffff;
  -webkit-transition: all .35s ease;
  -moz-transition: all .35s ease;
  -ms-transition: all .35s ease;
  -o-transition: all .35s ease;
  transition: all .35s ease;
}
#cssmenu.align-right ul ul li a {
  text-align: right;
}
#cssmenu ul ul li:hover > a {
  background: #f2f2f2;
  color: #8c9195;
}
#cssmenu ul ul li:last-child > a,
#cssmenu ul ul li.last > a {
  border-bottom: 0;
}
#cssmenu > ul > li > ul::after {
  content: '';
  border: 6px solid transparent;
  width: 0;
  height: 0;
  border-bottom-color: #ffffff;
  position: absolute;
  top: -12px;
  left: 30px;
}
#cssmenu.align-right > ul > li > ul::after {
  left: auto;
  right: 30px;
}
#cssmenu ul ul li.has-sub::after {
  border: 4px solid transparent;
  border-left-color: #9ea2a5;
  right: 10px;
  top: 12px;
  -moz-transition: all .2s ease;
  -ms-transition: all .2s ease;
  -o-transition: all .2s ease;
  transition: all .2s ease;
  -webkit-transition: -webkit-transform 0.2s ease, right 0.2s ease;
}
#cssmenu.align-right ul ul li.has-sub::after {
  border-left-color: transparent;
  border-right-color: #9ea2a5;
  right: auto;
  left: 10px;
}
#cssmenu ul ul li.has-sub:hover::after {
  border-left-color: #ffffff;
  right: -5px;
  -webkit-transform: rotateY(180deg);
  -ms-transform: rotateY(180deg);
  -moz-transform: rotateY(180deg);
  -o-transform: rotateY(180deg);
  transform: rotateY(180deg);
}
#cssmenu.align-right ul ul li.has-sub:hover::after {
  border-right-color: #ffffff;
  border-left-color: transparent;
  left: -5px;
  -webkit-transform: rotateY(180deg);
  -ms-transform: rotateY(180deg);
  -moz-transform: rotateY(180deg);
  -o-transform: rotateY(180deg);
  transform: rotateY(180deg);
}
@media all and (max-width: 800px), only screen and (-webkit-min-device-pixel-ratio: 2) and (max-width: 1024px), only screen and (min--moz-device-pixel-ratio: 2) and (max-width: 1024px), only screen and (-o-min-device-pixel-ratio: 2/1) and (max-width: 1024px), only screen and (min-device-pixel-ratio: 2) and (max-width: 1024px), only screen and (min-resolution: 192dpi) and (max-width: 1024px), only screen and (min-resolution: 2dppx) and (max-width: 1024px) {
  #cssmenu {
    width: auto;
  }
  #cssmenu.align-center ul {
    text-align: left;
  }
  #cssmenu.align-right > ul > li {
    float: none;
  }
  #cssmenu ul {
    width: auto;
  }
  #cssmenu .submenuArrow,
  #cssmenu #indicatorContainer {
    display: none;
  }
  #cssmenu > ul {
    height: auto;
    display: block;
  }
  #cssmenu > ul > li {
    float: none;
  }
  #cssmenu li,
  #cssmenu > ul > li {
    display: none;
  }
  #cssmenu ul ul,
  #cssmenu ul ul ul,
  #cssmenu ul > li:hover > ul,
  #cssmenu ul ul > li:hover > ul,
  #cssmenu.align-right ul ul,
  #cssmenu.align-right ul ul ul,
  #cssmenu.align-right ul > li:hover > ul,
  #cssmenu.align-right ul ul > li:hover > ul {
    position: relative;
    left: auto;
    top: auto;
    opacity: 1;
    padding-left: 0;
    padding-right: 0;
    right: auto;
  }
  #cssmenu ul .has-sub::after {
    display: none;
  }
  #cssmenu ul li a {
    padding: 12px 20px;
  }
  #cssmenu ul ul li a {
    border: 0;
    background: none;
    width: auto;
    padding: 8px 35px;
  }
  #cssmenu.align-right ul ul li a {
    text-align: left;
  }
  #cssmenu ul ul li:hover > a {
    background: none;
    color: #8c9195;
  }
  #cssmenu ul ul ul a {
    padding: 8px 50px;
  }
  #cssmenu ul ul ul ul a {
    padding: 8px 65px;
  }
  #cssmenu ul ul ul ul ul a {
    padding: 8px 80px;
  }
  #cssmenu ul ul ul ul ul ul a {
    padding: 8px 95px;
  }
  #cssmenu > ul > #menu-button {
    display: block;
    cursor: pointer;
  }
  #cssmenu #menu-button > a {
    padding: 14px 20px;
  }
  #cssmenu ul.open li,
  #cssmenu > ul.open > li {
    display: block;
  }
  #cssmenu > ul.open > li#menu-button > a {
    color: #fff;
    border-bottom: 1px solid rgba(150, 150, 150, 0.1);
  }
  #cssmenu ul ul::after {
    display: none;
  }
  #cssmenu #menu-button::after {
    display: block;
    content: '';
    position: absolute;
    height: 3px;
    width: 22px;
    border-top: 2px solid #7a8189;
    border-bottom: 2px solid #7a8189;
    right: 20px;
    top: 15px;
  }
  #cssmenu #menu-button::before {
    display: block;
    content: '';
    position: absolute;
    height: 3px;
    width: 22px;
    border-top: 2px solid #7a8189;
    right: 20px;
    top: 25px;
  }
  #cssmenu ul.open #menu-button::after,
  #cssmenu ul.open #menu-button::before {
    border-color: #fff;
  }
}

</style>
