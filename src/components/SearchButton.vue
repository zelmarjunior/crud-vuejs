<template>
    <div class="main-container">
      <button id="register-button" class="register-button" v-on:click='showForms'>
        Cadastrar Cliente
      </button>
      <button id="search-button" class="search-button" v-on:click='showwInputSearch'>
        Buscar com CPF
      </button>
      <input type="text" name="search" id="search">
    </div>
    
</template>

<script>
export default {
    name: "SearchButton",
    methods: {
        showwInputSearch() {
            document.getElementById("search").style.display = "flex";
            document.getElementById("register-button").style.display = "none";
        },

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
                        alert("CPF não cadastrado!");
                    }
                }
            } else {
                alert("Digite alguma coisa.");
            }
        },

        showForms() {
            this.clean();
            document.getElementById("search-button").style.display = "none";

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
    flex-direction: row;
    justify-content: center;
    align-items: center;
    /* background-color: black; */
}

#search {
    margin: 20px 20px;
    display: none;
}

.register-button,
.search-button {
    width: 100px;
    height: 100px;
    border-radius: 100%;
    border: 1px solid transparent;
    opacity: 0.8;
    padding: 10px;
    margin: 40px;
    color: #545454;
    font-weight: 700;
    font-size: 11px;
    background-color: aqua;
}

.register-button:hover,
.search-button:hover {
    opacity: 1;
    width: 95px;
    height: 95px;
    transition: 0.1s ease-in-out;
    cursor: pointer;
}
</style>