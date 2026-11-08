<template>
  <div class="grid min-h-dvh grid-cols-1 gap-8 lg:grid-cols-12">
    <div class="relative min-h-64 overflow-hidden lg:col-span-4">
      <img
        src="@/assets/images/thanksgiving dinner table.jpg"
        alt="A dinner table topped with traditional Thanksgiving fare"
        class="absolute insert-0 h-full w-full object-cover"
      />
    </div>
    <section class="min-w-0 px-6 py-8 lg:col-span-8 lg:px-12">
      <div><h2 class="font-display text-9xl text-center mb-4">Friendsgiving Day</h2></div>
      <div class="flex flex-col gap-6">
        <MenuItem title="Mashed Potatoes" subtitle="with Herbs and Gravy" />
        <MenuItem title="Cajun Seasoned Turkey Breast" />
        <MenuItem title="Glazed Ham" />
        <MenuItem
          title="Green Bean Casserole"
          subtitle="a casserole of Fresh Green Beans, Cream of Chicken Soup, Fried Onions, and Seasonings"
        />
        <MenuItem
          title="Macaroni and Cheese with Bacon"
          subtitle="sharp white cheddar and gruyere infused with a shallot and sage oil"
        />
        <MenuItem
          title="Sweet Potato Casserole"
          subtitle="a casserole of mashed yams, butter, brown sugar, topped with marshmallows allowed to toast lightly"
        />
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import MenuItem from '@/components/MenuItem.vue'
</script>

<style scoped></style>
