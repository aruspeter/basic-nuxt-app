<template>
  <div class="demo">
    <h1>This is a demo</h1>
    <div v-if="activeItem">
      <h2>This is an active item:</h2>
      <div class="grid-item active-item">
        <h3>{{ activeItem.title }}</h3>
        <p>{{ activeItem.body }}</p>
      </div>
    </div>
    <h2>Things I've just fetched:</h2>
    <div class="grid-holder">
      <template v-for="(item, index) in data.data">
        <div class="grid-item" :key="index" @click="activeItem = item">
          <h3>{{ item.title }}</h3>
          <p>{{ item.body }}</p>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloPage',
  props: {
    data: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      activeItem: null,
    }
  },
}
</script>

<style lang="scss" scoped>
.demo {
  padding: 30px;
}
h3 {
  font-size: 20px;
}
.grid-holder {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(3, 1fr);
}
.grid-item {
  padding: 20px;
  border: 1px solid black;
  border-radius: 5px;
  transition: all 0.5s;
  &:hover {
    background-color: rgb(233, 209, 255);
    transform: scale(1.05);
  }
}
.active-item {
  max-width: 300px;
}
</style>
