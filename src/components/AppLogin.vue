<template>
	<div class="home">
		<app-toolbar></app-toolbar>
			<h1>This is a login page</h1>
		<app-footer></app-footer>

		<v-form>
    <v-container>
      <v-row>
        <v-col
          cols="12"
          sm="6"
          md="3"
        >
          <v-text-field
            label="Username"
          ></v-text-field>
        </v-col>
    </v-row>


     <v-row>
        <v-col
          cols="12"
          sm="6"
          md="3"
        >
          <v-text-field
            label="Password"
            type="password"
          ></v-text-field>
        </v-col>
    </v-row>

    <v-btn block>Login</v-btn>
</v-container>
</v-form>
		
	</div>

</template>

<script>
//step 1
import AppFooter from './AppFooter.vue';
import AppToolbar from './AppToolbar.vue';
export default {
	name: 'AppLogin',
	components: {AppFooter, AppToolbar}
	//2) Declare appfooter and apptoolbar in components
}

</script>