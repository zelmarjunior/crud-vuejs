<template>
    <div class="main-container">
      <h1>Cadastrar Cliente</h1>
      <button id="button" class="register-button" v-on:click='showForms'>
        ADD
      </button>
      <h1>Buscar com CPF</h1>
      <button id="button" class="register-button" v-on:click='getDataInputSearch'>
        BUSCAR
      </button>
      <input type="text" name="search" id="search">
    </div>
    
</template>

<script>
export default {
    name: "SearchButton",
    methods: {
        getDataInputSearch() {
            let searchData = document.getElementById("search").value;
            if (searchData) {
                const customers = JSON.parse(localStorage.getItem("customers"));

                for (const customer of customers) {
                    /* console.log(customer) */
                    if (customer.customerCpf == searchData) {
                        document.getElementsByClassName(
                            "form-main-container"
                        )[0].style.display = "flex";
                        document.getElementById("updateButton").style.display =
                            "flex";
                        document.getElementById(
                            "registerButton"
                        ).style.display = "none";
                        alert("achei um cara");
                        document.getElementById("cpf").value =
                            customer.customerCpf;
                        document.getElementById("name").value =
                            customer.customerFullName;
                        document.getElementById("adress").value =
                            customer.customerAdress;
                        document.getElementById("adressNumber").value =
                            customer.customerAdressNumber;
                        document.getElementById("district").value =
                            customer.customerDistrict;
                        document.getElementById("complement").value =
                            customer.customerComplement;
                        document.getElementById("city").value =
                            customer.customerCity;
                        document.getElementById("postalCode").value =
                            customer.customerPostalCode;
                        document.getElementById("phone").value =
                            customer.customerPhone;
                        document.getElementById("mobilePhone").value =
                            customer.customerMobilePhone;
                        document.getElementById("dateOfBirth").value =
                            customer.customerDateOfBirth;
                        document.getElementById("email").value =
                            customer.customerEmail;
                        document.getElementById("salary").value =
                            customer.customerSalary;
                        document.getElementById("rg").value =
                            customer.customerRg;

                        break;
                    } else {
                        alert("nao achei nenhum");
                    }
                }
            } else {
                alert("Digite alguma coisa.");
            }
        },

        showForms() {
            this.clean();

            document.getElementsByClassName(
                "form-main-container"
            )[0].style.display = "flex";
            document.getElementById("registerButton").style.display = "flex";
            document.getElementById("updateButton").style.display = "none";
        },
        clean() {
            document.getElementById("cpf").value = "";
            document.getElementById("name").value = "";
            document.getElementById("adress").value = "";
            document.getElementById("adressNumber").value = "";
            document.getElementById("district").value = "";
            document.getElementById("complement").value = "";
            document.getElementById("city").value = "";
            document.getElementById("postalCode").value = "";
            document.getElementById("phone").value = "";
            document.getElementById("mobilePhone").value = "";
            document.getElementById("dateOfBirth").value = "";
            document.getElementById("email").value = "";
            document.getElementById("salary").value = "";
            document.getElementById("rg").value = "";
        },
    },
};
</script>

<style scoped>
.main-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    
}

#search {
    margin: 0 20px;
}

.register-button {
    /*    display: flex;
    justify-content: center;
    align-content: center;
    /* border: solid 1px#545454; */
    /* background-color: #545454;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    font-size: 44px;
    cursor: pointer; */
}

h1 {
    color: black;
    font-size: 20px;
}
</style>