<template>
  <div class="flex flex-1 flex-col justify-center px-4 lg:px-16 w-full max-md:px-5 max-md:max-w-full">
    <div class="max-md:mr-1 max-md:max-w-full">
      <div class="grid grid-cols-1 lg:grid-cols-5 gap-5 gap-y-7 max-md:flex-col max-md:gap-0">
        <article v-for="item in transformedItems" :key="item.id" class="flex flex-col w-full max-md:w-full">
          <div class="flex flex-col grow">
            <div
              class="flex overflow-hidden relative flex-col items-end pt-3.5 pr-4 pb-10 lg:pb-20 pl-4 lg:pl-16 w-full aspect-square max-md:pl-5">
              <img loading="lazy" :src="item.thumbnail" :alt="item.thumbnail"
                class="object-cover rounded-2xl absolute inset-0 w-full h-full" />
              <img loading="lazy"
                src="https://cdn.builder.io/api/v1/image/assets/TEMP/65307df6be7d388d5052a6761292e471635a623b0592318cb2801e949a43f150?apiKey=c7a92bb848a54e2a9467c51b088c741f&"
                alt="" class="mb-5 lg:mb-10 w-8 aspect-square max-md:mb-10 z-10" />
            </div>
            <div class="flex flex-col gap-3 lg:gap-5 justify-between mt-2 w-full max-md:flex-row max-md:gap-0">
              <div class="flex flex-col pr-2 text-xs text-neutral-800 max-md:w-full w-full">
                <div class="flex justify-between">
                  <h3 class="text-base whitespace-nowrap font-semibold">{{ item.title }}</h3>
                  <div class="flex">
                    <img loading="lazy"
                      src="https://cdn.builder.io/api/v1/image/assets/TEMP/988135a769986d2daa92fdf57fb05dcd5538cf8aeec16e44f28a21f0ebfa94ce?apiKey=c7a92bb848a54e2a9467c51b088c741f&"
                      alt="" class="shrink-0 my-auto w-3 aspect-square" />
                    <p class="grow self-center font-semibold">{{ item.rating }}</p>
                  </div>
                </div>
                <p class="mt-1 whitespace-nowrap text-neutral-500 text-[0.9375rem]">{{ item.category }}</p>
                <p class="mt-1 text-neutral-500 text-[0.9375rem]">{{ item.brand }} </p>
                <p class="mt-2 text-sm whitespace-nowrap underline">
                  <span class="font-semibold text-[0.9375rem] text-neutral-800 ">${{ item.price }}</span>
                  total
                </p>
              </div>
            </div>
          </div>
        </article>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'DestinationCards',
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
        const response = await fetch('https://dummyjson.com/products');
        if (!response.ok) {
          throw new Error('Failed to fetch categories');
        }
        const data = await response.json();
        this.items = data.products;
      } catch (error) {
        console.error(error);
      }
    }
  },
  computed: {
    transformedItems() {
      // Using map function to transform items
      return this.items.map(item => {
        return {
          id: item.id,
          title: item.title,
          thumbnail: item.thumbnail,
          description: item.description,
          price: item.price,
          discountPercentage: item.discountPercentage,
          rating: item.rating,
          stock: item.stock,
          brand: item.brand,
          category: item.category,
          thumbnail: item.thumbnail,
          images: item.image
        };
      });
    }
  }
});
</script>./Body.vue