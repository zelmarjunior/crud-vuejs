<template>
    <div class="form-main-container">
    <form>
      <section>
        <div class="input-container">
          <label for="cpf">CPF: </label>
          <input type="text" name="cpf" id="cpf" v-model="cpf" />
        </div>
        <div class="input-container">
          <label for="name">Nome:</label>
          <input type="text" name="name" id="name" v-model="fullName" />
        </div>
        <div class="input-container">
          <label for="email">E-mail: </label>
          <input type="text" name="email" id="email" v-model="email" />
        </div>
      </section>

      <section>
        <div class="input-container">
          <label for="adress">Endereço: </label>
          <input type="text" name="adress" id="adress" v-model="adress" />
        </div>
        <div class="input-container">
          <label for="adressNumber">Nº: </label>
          <input type="text" name="adressNumber" id="adressNumber" v-model="adressNumber" />
        </div>
        <div class="input-container">
          <label for="district">Bairro: </label>
          <input type="text" name="district" id="district" v-model="district" />
        </div>
      </section>

      <section>
        <div class="input-container">
          <label for="complement">Complemento: </label>
          <input type="text" name="complement" id="complement" v-model="complement" />
        </div>
        <div class="input-container">
          <label for="city">Cidade: </label>
          <input type="text" name="city" id="city" v-model="city" />
        </div>
        <div class="input-container">
          <label for="postalCode">CEP: </label>
          <input type="text" name="postalCode" id="postalCode" v-bind="postalCode" />
        </div>
      </section>

      <section>
        <div class="input-container">
          <label for="phone">Telefone: </label>
          <input type="text" name="phone" id="phone" v-model="phone" />
        </div>
        <div class="input-container">
          <label for="mobilePhone">Celular: </label>
          <input type="text" name="mobilePhone" id="mobilePhone" v-model="mobilePhone" />
        </div>
        <div class="input-container">
          <label for="dateOfBirth">Data de Nascimento: </label>
          <input type="date" name="dateOfBirth" id="dateOfBirth" v-model="dateOfBirth" />
        </div>
      </section>

      <section>
        
        <div class="input-container">
          <label for="salary">Salário: </label>

          <input type="text" name="salary" id="salary" v-model="salary" />
        </div>
        <div class="input-container">
          <label for="rg">RG: </label>
          <input type="text" name="rg" id="rg" v-model="rg" />
        </div>
        
      </section>
      <div>

        <button id="registerButton" v-on:click='registerCustomer($event)' style="display: none;">Cadastrar</button>
        <button id="updateButton" v-on:click='updateCustomer($event)' style="display: none;">Editar</button>

        <a @click='loga'>Voltar</a>

      </div>
    </form>

    </div>
</template>

<script>
/* import CustomerData from './CustomerData.vue' */

export default {
    name: "InputForm",
    components: {},
    props: {},
    data() {
        return {
            id: "",
            fullName: "",
            adress: "",
            adressNumber: "",
            district: "",
            complement: "",
            city: "",
            postalCode: "",
            cpf: "",
            rg: "",
            phone: "",
            mobilePhone: "",
            dateOfBirth: "",
            email: "",
            salary: "",
            customers: [],
        };
    },
    methods: {
        registerCustomer(e) {
            e.preventDefault();
            console.log(this.dataOption);

            const customer = {
                customerId: this.id,
                customerCpf: this.cpf,
                customerFullName: this.fullName,
                customerAdress: this.adress,
                customerAdressNumber: this.adressNumber,
                customerDistrict: this.district,
                customerComplement: this.complement,
                customerCity: this.city,
                customerPostalCode: this.postalCode,
                customerRg: this.rg,
                customerPhone: this.phone,
                customerMobilePhone: this.mobilePhone,
                customerDateOfBirth: this.dateOfBirth,
                customerEmail: this.email,
                customerSalary: this.salary,
            };
            if (customer.customerCpf) {
                let customerStorage = JSON.parse(
                    localStorage.getItem("customers")
                );
                for (const customer of customerStorage) {
                    if (customer.customerCpf == this.cpf) {
                        return alert("CPF já cadastrado");
                    }
                }
                this.customers.push(customer);
                console.log("Cliente Adicionado");
                console.log(this.customers);
                localStorage.setItem(
                    "customers",
                    JSON.stringify(this.customers)
                );
                console.log();
                this.cleanForm();
            } else {
                alert("Digite um CPF");
            }
        },
        deleteCustomer(index) {
            this.customers.splice(index, 1);
            console.log("Cliente Deletadp");
            console.log(this.customers);
            this.cleanForm();
        },
        updateCustomer(e) {
            e.preventDefault();
            console.log("To dentro do update");

            const customer = {
                customerId: this.id,
                customerCpf: this.cpf,
                customerFullName: this.fullName,
                customerAdress: this.adress,
                customerAdressNumber: this.adressNumber,
                customerDistrict: this.district,
                customerComplement: this.complement,
                customerCity: this.city,
                customerPostalCode: this.postalCode,
                customerRg: this.rg,
                customerPhone: this.phone,
                customerMobilePhone: this.mobilePhone,
                customerDateOfBirth: this.dateOfBirth,
                customerEmail: this.email,
                customerSalary: this.salary,
            };
            if (customer.customerCpf) {
                let customerStorage = JSON.parse(
                    localStorage.getItem("customers")
                );
                for (let index = 0; index < customerStorage.length; index++) {
                    const customer = customerStorage[index];
                    if (customer.customerCpf == this.cpf) {
                        console.log(customerStorage);
                        customerStorage.splice(customerStorage[index], 1);
                        this.customers = customerStorage;
                        console.log("Cliente Editado");
                        console.log(this.customers);
                        localStorage.setItem(
                            "customers",
                            JSON.stringify(this.customers)
                        );
                        console.log();
                        this.cleanForm();
                        alert("alterado");
                    }
                }
            } else {
                alert("nao pode deixar cpf vazio seu nbosta");
            }

            /* this.customers.push(); */

            this.cleanForm();
        },
        cleanForm() {
            this.fullName = "";
            this.id = "";
            this.fullName = "";
            this.adress = "";
            this.adressNumber = "";
            this.district = "";
            this.complement = "";
            this.city = "";
            this.postalCode = "";
            this.cpf = "";
            this.rg = "";
            this.phone = "";
            this.mobilePhone = "";
            this.dateOfBirth = "";
            this.email = "";
            this.salary = "";
        },
        getData() {
            console.log(this.fullName);
        },
    },
};
</script>

<style scoped>
.table {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border: solid 1px black;
}

form {
    border: solid 1px black;
    padding: 30px;
}

table {
    text-align: center;
}

td {
    width: 250px;
}
.form-main-container {
    display: none;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 50px;
}

.input-container {
    display: flex;
    flex-direction: column;
}

section {
    display: flex;
}

input {
    margin: 10px 10px;
}
</style>