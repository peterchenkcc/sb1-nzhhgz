<template>
  <Page>
    <ActionBar class="bg-blue-600">
      <GridLayout columns="auto, *" class="w-full">
        <Label col="0" text="CruiseBooking" class="font-bold text-lg text-white p-2"/>
        <Label col="1" text="🔍" class="text-lg text-white text-right p-2 mr-2"/>
      </GridLayout>
    </ActionBar>

    <ScrollView>
      <StackLayout class="p-4">
        <!-- Search Section -->
        <StackLayout class="bg-white rounded-lg p-4 shadow-md mb-4">
          <Label text="Find Your Dream Cruise" class="text-xl font-bold mb-2 text-blue-800"/>
          <TextField hint="Where to?" class="border rounded p-2 mb-2"/>
          <TextField hint="When?" class="border rounded p-2 mb-2"/>
          <Button text="Search Cruises" class="bg-blue-600 text-white font-bold py-2 rounded"/>
        </StackLayout>

        <!-- Featured Deals -->
        <Label text="Featured Deals" class="text-lg font-bold mb-2 text-gray-800"/>
        <ScrollView orientation="horizontal" class="mb-4">
          <StackLayout orientation="horizontal">
            <StackLayout v-for="(deal, index) in featuredDeals" :key="index" 
                        class="mr-4 bg-white rounded-lg shadow-md" width="300">
              <Image :src="deal.image" stretch="aspectFill" height="150" class="rounded-t-lg"/>
              <StackLayout class="p-3">
                <Label :text="deal.destination" class="font-bold text-blue-800"/>
                <Label :text="deal.duration" class="text-gray-600"/>
                <Label :text="'From $' + deal.price" class="font-bold text-green-600"/>
              </StackLayout>
            </StackLayout>
          </StackLayout>
        </ScrollView>

        <!-- Popular Destinations -->
        <Label text="Popular Destinations" class="text-lg font-bold mb-2 text-gray-800"/>
        <GridLayout columns="*, *" rows="auto, auto" class="mb-4">
          <StackLayout v-for="(dest, index) in popularDestinations" :key="index"
                      :col="index % 2" :row="Math.floor(index / 2)"
                      class="m-1 bg-white rounded-lg shadow-md">
            <Image :src="dest.image" stretch="aspectFill" height="100" class="rounded-t-lg"/>
            <Label :text="dest.name" class="p-2 font-bold text-center"/>
          </StackLayout>
        </GridLayout>
      </StackLayout>
    </ScrollView>
  </Page>
</template>

<script lang="ts">
import Vue from "nativescript-vue";

export default Vue.extend({
  data() {
    return {
      featuredDeals: [
        {
          destination: "Caribbean Paradise",
          duration: "7 Nights",
          price: "599",
          image: "~/images/caribbean.jpg"
        },
        {
          destination: "Mediterranean Dream",
          duration: "10 Nights",
          price: "899",
          image: "~/images/mediterranean.jpg"
        },
        {
          destination: "Alaska Adventure",
          duration: "8 Nights",
          price: "799",
          image: "~/images/alaska.jpg"
        }
      ],
      popularDestinations: [
        { name: "Caribbean", image: "~/images/caribbean.jpg" },
        { name: "Mediterranean", image: "~/images/mediterranean.jpg" },
        { name: "Alaska", image: "~/images/alaska.jpg" },
        { name: "Hawaii", image: "~/images/hawaii.jpg" }
      ]
    };
  }
});
</script>