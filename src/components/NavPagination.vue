<template>
    <div class="pagination-container">
      <button class="goPrev" @click="handlePrevClick" :disabled="isPrevDisabled">
        &lt;
      </button>
      <div class="pagination">
        <button
          v-for="(item, index) in visibleItems"
          :key="index"
          class="pagination__item"
          :class="{ 'pagination__item_active': item === activePage }"
          @click="handleNumBtnClick(item)"
        >
          {{ item }}
        </button>
      </div>
      <button class="goNext" @click="handleNextClick" :disabled="isNextDisabled">
        &gt;
      </button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      min: {
        type: Number,
        required: true,
        default: 1
      },
      max: {
        type: Number,
        required: true,
        default:10
      },
    },
    data() {
      return {
        activePage: this.min,
      };
    },
    computed: {
      visibleItems() {
        const start = Math.max(this.activePage - 2, this.min);
        const end = Math.min(start + 4, this.max);
        const items = [];
        for (let i = start; i <= end; i++) {
          items.push(i);
        }
        return items;
      },
      isPrevDisabled() {
        return this.activePage === this.min;
      },
      isNextDisabled() {
        return this.activePage === this.max;
      },
    },
    methods: {
      handleNumBtnClick(item) {
        this.activePage = item;
      },
      handlePrevClick() {
        if (!this.isPrevDisabled) {
          this.activePage -= 1;
        }
      },
      handleNextClick() {
        if (!this.isNextDisabled) {
          this.activePage += 1;
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .pagination-container {
    display: flex;
    align-items: center;
  }
  
  .goPrev,
  .goNext,
  .pagination__item {
    border: none;
    background-color: #fff;
    cursor: pointer;
    padding: 8px 12px;
    margin: 4px;
    display: flex;
    align-items: center;
    color: #000;
    border-radius: 50%;
  }
  
  .pagination__item_active {
    background-color: #886cc0;
    color: #fff;
  }
  .pagination{
    display: flex;
  }
.goPrev,.goNext{
    border: 1px solid #886cc0;
    background-color: #ebd6f7;
}

</style>