<template>
  <footer class="flex gap-2 px-16 py-4 text-xs whitespace-nowrap bg-white mt-10 max-md:flex-wrap max-md:px-5 max-md:mt-10">
    <div class="flex flex-auto gap-2 self-start pr-20 text-neutral-500 max-md:flex-wrap">
      <div>© 2022 Airbnb, Inc.</div>
      <div class="justify-center pl-1.5">Privacy</div>
      <div class="justify-center pl-1.5">Terms</div>
      <div class="justify-center pl-1.5">Sitemap</div>
      <div class="justify-center pl-1.5">Company details</div>
      <div class="justify-center pl-1.5">Destinations</div>
    </div>
    <div class="flex shrink gap-5 justify-between font-semibold basis-auto grow-0 text-neutral-800">
      <div class="flex gap-1">
        <img loading="lazy" src="https://cdn.builder.io/api/v1/image/assets/TEMP/2a4f96500c2dba3bb259701aea622269a7b681b59a7768b08de878fcffa44e37?apiKey=c7a92bb848a54e2a9467c51b088c741f&" alt="Globe icon" class="shrink-0 w-4 aspect-square" />
        <div class="grow">English (IN)</div>
      </div>
      <div>INR</div>
      <div class="flex gap-1">
        <div class="grow">Support & resources</div>
        <img loading="lazy" src="https://cdn.builder.io/api/v1/image/assets/TEMP/46d996eaf8d4dab5c863d58e2f42f9f9399f9d607091c30f3f6932ed1c91cada?apiKey=c7a92bb848a54e2a9467c51b088c741f&" alt="Chevron up icon" class="shrink-0 w-4 aspect-square" />
      </div>
    </div>
  </footer>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Footer',
});
</script>./Footer.vue