<script>
import Item from './components/Item.vue'

export default {
  name: 'App',
  components: {
    Item
  },
  computed: {
    leftMocData() {
      return [
        {
          "id": 1,
          "name": "Shoes 1"
        },
        {
          "id": 2,
          "name": "Shoes 2"
        },
        {
          "id": 3,
          "name": "Shoes 3"
        },
        {
          "id": 4,
          "name": "Shoes 4"
        },
        {
          "id": 5,
          "name": "T-shirt 1"
        },
        {
          "id": 6,
          "name": "T-shirt 2"
        },
        {
          "id": 7,
          "name": "T-shirt 3"
        },
        {
          "id": 8,
          "name": "T-shirt 4"
        }
      ]
    },
    rightMocData() {
      return [
        {
          "id": 11,
          "name": "Jacket 1"
        },
        {
          "id": 12,
          "name": "Jacket 2"
        },
        {
          "id": 13,
          "name": "Jacket 3"
        },
        {
          "id": 14,
          "name": "Jacket 4"
        },
        {
          "id": 15,
          "name": "Hoodie 1"
        },
        {
          "id": 16,
          "name": "Hoodie 2"
        },
        {
          "id": 17,
          "name": "Hoodie 3"
        },
        {
          "id": 18,
          "name": "Hoodie 4"
        }
      ]
    },
  },
  data() {
    return {
      leftSelectedItems: [],
      rightSelectedItem: null,
    }
  },
  methods: {
    manyItemSelector(evt, data) {
      if(evt.currentTarget.classList.contains('selected')) return false
      this.leftSelectedItems.push(data)
      this.leftSelectedItems = this.leftSelectedItems.slice(-6)
    },
    singleItemSelector(evt, data) {
      if(evt.currentTarget.classList.contains('selected')) return false
      this.rightSelectedItem = data
    },
  },
}
</script>

<template>
  <div class="top-wrapper">
    <div class="column">
      <Item
          v-for="data in leftSelectedItems"
          :data="data"
      />
    </div>
    <div class="column">
      <Item
          :data="rightSelectedItem"
      />
    </div>

  </div>
  <div class="middle-wrapper">
    <div class="column">
      <Item
          v-for="data in leftMocData"
          :class="{selected: !!this.leftSelectedItems.filter(el => el.id === data.id).length}"
          :data="data"
          @click="(evt) => manyItemSelector(evt, data)"
      />
    </div>
    <div class="column">
      <Item
          v-for="data in rightMocData"
          :class="{selected: data.id === rightSelectedItem?.id}"
          :data="data"
          @click="(evt) => singleItemSelector(evt, data)"
      />
    </div>
  </div>
  <Item/>
</template>

<style lang="scss" scoped>
.top-wrapper {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
  width: 100%;
  max-width: 1440px;
  margin: 0 auto;
  .column {
    display: flex;
    gap: 10px;
    padding: 10px;
    border: #ccc 1px solid;
  }
}
.middle-wrapper {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
  width: 100%;
  max-width: 1440px;
  margin: 0 auto;

  .column {
    display: flex;
    gap: 10px;
    padding: 10px;
    border: #ccc 1px solid;
  }
}

</style>
