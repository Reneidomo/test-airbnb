<template>
  <section
    class="flex gap-5 justify-between items-center px-16 py-7 text-xs text-black whitespace-nowrap max-md:flex-wrap max-md:px-5">
    <div class="flex w-full overflow-hidden">
      <article class="text-center px-4" v-for="item in transformedItems" :key="item.id">
        <div class="flex">
          <img loading="lazy" :src="item.src" alt="Camping" class="self-center w-6 aspect-square m-auto" />
        </div>
        <p class="mt-1">{{ item.name }}</p>
      </article>
    </div>

    <div class="flex gap-4 self-stretch text-neutral-800">
      <img loading="lazy"
        src="https://cdn.builder.io/api/v1/image/assets/TEMP/2f957f8417ea975dfa49fe3238b564407a0a4d74cc753185275331442f5931e1?apiKey=c7a92bb848a54e2a9467c51b088c741f&"
        alt="" class="shrink-0 my-auto w-6 aspect-square border-zinc-400" />
      <button class="flex w-[100px] gap-2 px-2 py-4 bg-white rounded-lg border border-solid border-zinc-300">
        <img loading="lazy"
          src="https://cdn.builder.io/api/v1/image/assets/TEMP/0ed5a4d7ab458d6128b66ec8ab0fa4ee5daac55b9be2a5f07aba39b0a61597c3?apiKey=c7a92bb848a54e2a9467c51b088c741f&"
          alt="" class="shrink-0 w-4 aspect-square" />
        <span>Filters</span>
      </button>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'CategorySection',
  data() {
    return {
      items: []
    };
  },
  mounted() {
    this.fetchCategories();
  },
  methods: {
    async fetchCategories() {
      try {
        const response = await fetch('https://dummyjson.com/products/categories');
        if (!response.ok) {
          throw new Error('Failed to fetch categories');
        }
        const data = await response.json();
        this.items = data;
      } catch (error) {
        console.error(error);
      }
    }
  },
  computed: {
    transformedItems() {
      // Using map function to transform items
      return this.items.map((item, index) => {
        return {
          id: index,
          name: item,
          src: "https://a0.muscache.com/pictures/732edad8-3ae0-49a8-a451-29a8010dcc0c.jpg"
        };
      });
    }
  }
});
</script>./Category.vue
