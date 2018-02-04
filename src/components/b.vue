<template>
  <div class="bl">
      <ul>
          <li v-for="item in list" :key="item.name">{{item.name}}:{{item.price}}
              <button @click="emit">emit</button>
          </li>
      </ul>
{{myValue}}
  </div>
</template>

<script>
export default {
  props: {
    'my-value': [String]
  },
  data () {
    return {
      list: [
        { name: 'banana', price: 24 },
        { name: 'apple', price: 22 },
        { name: 'orange', price: 12 },
        { name: 'fish', price: 20 },
        { name: 'rou', price: 30 }
      ]
    }
  },
  methods: {
    emit () {
      this.$emit('my-event', ' hello world')
    }
  }
}
</script>

<style>
.bl {
  margin: 20px 0 0 20px;
}
.bl ul {
  list-style: none;
}
</style>
