<template>
  <div>
    <header>
      <SearchButton v-on:click='openRegisterModal' />
      <InputForm id='modal'/>
      
    </header>
  </div>
</template>

<script>
/* import DashboardView from './components/DashboardView.vue'; */
import SearchButton from "./components/SearchButton.vue";
import InputForm from "./components/InputForm.vue";

export default {
    name: "App",
    components: {
        /* DashboardView, */
        SearchButton,
        InputForm,
    }
};
</script>

<style scoped>
header {
    display: flex;
    flex-direction: column;;

}
</style>
