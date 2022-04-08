<template>
  <div>
    <header>
      <SearchButton v-on:click='openRegisterModal' />
      <DashboardView />
      <InputForm id='modal' :PropOption="this.stadoOption" style="display:none;" />
      
    </header>
  </div>
</template>

<script>
import DashboardView from './components/DashboardView.vue';
import SearchButton from "./components/SearchButton.vue";
import InputForm from "./components/InputForm.vue";

export default {
    name: "App",
    components: {
        DashboardView,
        SearchButton,
        InputForm,
    },
    data() {
        return {
            customers: [],
            stadoOption: '',
            
        };
    },
    methods: {
        
        openRegisterModal() {
          this.stadoOption = 'Cadastrar'
          console.log(this.stadoOption)
          document.getElementById('modal').style.display = 'flex';
        },
    },
};
</script>
