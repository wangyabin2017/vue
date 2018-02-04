<template>

<div class="">
  <button @click="show = !show">Toggle</button>
  <div class="ab">
    <transition @before-enter="beforeEnter" @enter="enter" @leave="leave" :css="false">
      <!-- <div :is="component"></div> -->
      <p class="animation-p" v-show="show" v-color="'blue'">i am show</p>
    </transition>
      <input type="text" v-focus>
  </div>
    <!-- <p is="comp-a"></p>
    <input type="text" @keyup.13="add" >
    <p v-for= " (item, index) in arr" :key="index">{{ index }} {{ item }}</p>
    <list @my-event="onconevent" :my-value="text"></list>
    <input type="text" v-model.number="text">

    {{contuntText}} -->

</div>
</template>

<script>
// import Vue from 'vue'
import CompA from './components/a'
import list from './components/b'
export default {
  components: { CompA, list },
  directives: {
    focus: {
      inserted: function (el, binding){
        el.focus()
      }
    },
    color: function (el, binding) {
      el.style.color = binding.value
    }
  },
  data () {
    return {
      show: true,
      component: 'comp-a'
      // hello: 'hello world',
      // status: true,
      // text: '',
      // arr: ['123', '456', '789'],
      // odjlist: {
      //   name: 'apple',
      //   price: '20',
      //   color: 'red',
      //   weight: '14'
      //  }
    }
  },
  methods: {
    mycl () {
      if (this.component === 'comp-a') {
        this.component = 'list'
      } else {
        this.component = 'comp-a'
      }
    },
    beforeEnter (el) {
      $(el).css({left: '-600px', opacity: 0})
    },
    enter (el, done) {
      $(el).animate({
        left: '10px',
        opacity: 1
      }, {
        duration: 1500,
        complete: done
      })
    },
    leave (el, done) {
      $(el).animate({
        left: '600px',
        opacity: 0
      }, {
        duration: 1500,
        complete: done
      })
    }
    //   addItem () {
    //     Vue.set(this.arr, 1, this.text)
    //   },
    //   add (e) {
    //     // console.log(e.target.value)
    //     Vue.set(this.arr, 1, e.target.value)
    //   },
    //   onconevent (obj) {
    //     console.log('onconevent' + obj)
    //   }
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin: 0 auto;
}
.ab {
  text-align: center;
}
.fade-enter-active,
.fade-leave-active {
  transition: all 0.4s;
}
.fade-enter,
.fade-leave-active {
  animation: bocun-in 0.5s;
}
@keyframes bocun-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}

.animation-p{
  /* width: 200px; */
  position: absolute;
  top: 200px;
  left: 10px;
}

.my-trans-enter-active,
.my-trans-leave-active {
  transition: all 0.4s ease-out;
}
.my-trans-enter {
  transform: translateY(-500px);
  opacity: 0;
}
.my-trans-leave {
  transform: translateY(500px);
  opacity: 0;
}
</style>
