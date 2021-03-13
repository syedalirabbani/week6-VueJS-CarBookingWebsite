<template>
	<div class="home">
		<app-toolbar></app-toolbar>
		<v-carousel>
			<v-carousel-item
			v-for="(item,i) in items"
			:key="i"
			:src="item.src"
			reverse-transition="fade-transition"
			transition="fade-transition"
			></v-carousel-item>
		</v-carousel>
		<section id="cars" class="text-center">
			<v-container>
				<h3>Book a car now!</h3>
				<v-row>
					<v-col
					cols="4">
					<v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="374"
    v-for = "car in cars"
    :key = "car.name"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      height="250"
      v-bind:src = "car.imageurl"

    ></v-img>

    <v-card-title>Perodua Alza</v-card-title>

    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >
        <v-rating
          :value="car.rating"
          color="amber"
          dense
          half-increments
          readonly
          size="14"
        ></v-rating>

        <div class="grey--text ml-4 ">Rating : {{car.rating}}</div>


        
      </v-row>

      

      <div>{{car.price}}</div>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    

    

    <v-card-actions>
      <v-btn
        color="deep-purple lighten-2"
        text
        @click="reserve"
      >
        Reserve
      </v-btn>
    </v-card-actions>
  </v-card>
	</v-col>
				
	</v-row>
</v-container>


</section>
<app-footer></app-footer>

</div>

</template>

<script>
//step 1
import AppFooter from './AppFooter.vue';
import AppToolbar from './AppToolbar.vue';
export default {
	name: 'AppHome',
	components: {AppFooter, AppToolbar},
	data() {
		return {
			cars: [

			{
				name : "Perodua Alza",
				location : "Johor",
				description : " Perodua Alza sesuai untuk 4 orang",
				price : "RM80 per day",
				rating : 4,
				imageurl : "https://s4.paultan.org/image/2018/09/2018-Perodua-Alza-AV-facelift-1-e1536119391982.jpg"

			},

			{
				name : "Perodua Viva",
				location : "Johor",
				description : " Perodua Viva sesuai untuk 4 orang",
				price : "RM50 per day",
				rating : 3.5,
				imageurl : "http://paultan.org/images.paultan.org/images/d18d_viva/Perodua_Viva_34_Back.jpg"

			},

			{
				name : "Proton Saga",
				location : "Johor",
				description : " Proton Saga sesuai untuk 4 orang",
				price : "RM90 per day",
				rating : 4,
				imageurl : "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQFyNV5SBqPl2_USq9l61QPuJVrqdN8FHSmhQC9lhH_Ro3vlKgXWQqS5YoZr19Ny1kRp3c&usqp=CAU"

			}

			],
			items: [
			{
				src: 'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg',
			},
			{
				src: 'https://cdn.vuetifyjs.com/images/carousel/sky.jpg',
			},
			{
				src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg',
			},
			{
				src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg',
			},
			],
		}
	}
	
}

</script>