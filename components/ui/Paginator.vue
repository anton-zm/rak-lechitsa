<template>
  <div class="container">
    <ul class="nav">
      <li
        v-for="index in pagesCount"
        :key="index"
        @click="setActive(index)"
        :class="['nav__item', { nav__item_active: index === active }]"
      >
        {{ index }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    totalItems: {
      type: Number,
      default: 0,
    },
    itemsPerPage: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      active: 1,
    };
  },
  computed: {
    pagesCount() {
      return Math.ceil(this.totalItems / this.itemsPerPage);
    },
  },
  methods: {
    setActive(index) {
      this.active = index;
      this.$emit('OnPageChanged', index);
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
.nav {
  display: inline-block;
  list-style-type: none;
}
.nav__item {
  width: 58px;
  height: 58px;
  background: #fbfbfb;
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 22px;
  cursor: pointer;
  display: inline-block;
  padding-top: 20px;
  padding-left: 25px;
  margin-right: 10px;
  color: #000;
  transition: 0.3s;
}
.nav__item:hover {
  background: #f4f4f4;
}
.nav__item_active {
  background: #f4f4f4;
}
@media (max-width: 1440px) {
}
@media (max-width: 1280px) {
}
@media (max-width: 1024px) {
  .nav__item {
    width: 50px;
    height: 50px;
    font-weight: 500;
    font-size: 15px;
    line-height: 18px;
    padding-top: 18px;
    padding-left: 22px;
  }
}
@media (max-width: 768px) {
}
@media (max-width: 425px) {
}
</style>
