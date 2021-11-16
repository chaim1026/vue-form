<template>
    <v-card
    class="card-width"
    elevation="2"
    outlined
    >
        <ValidationObserver v-slot="{ handleSubmit }">
            <form @submit.prevent="handleSubmit(onSubmit)">
                <ValidationProvider name="First Name" rules="required|alpha" v-slot="{ errors }">
                    <div class="input">
                        <v-text-field
                            label="First Name"
                            type="text"
                            v-model="formData.firstName"
                            outlined
                        ></v-text-field>
                        <span>{{errors[0]}}</span>
                    </div>
                </ValidationProvider>

                <ValidationProvider name="Last Name" rules="required|alpha" v-slot="{ errors }">
                    <div  class="input">
                        <v-text-field
                            label="Last Name"
                            type="text"
                            v-model="formData.lastName"
                            outlined
                        ></v-text-field>
                        <span>{{errors[0]}}</span>
                    </div>
                </ValidationProvider>

                <ValidationProvider name="Email" rules="required|email" v-slot="{ errors }">
                    <div class="input">
                        <v-text-field
                            label="Email"
                            type="email"
                            v-model="formData.email"
                            outlined
                        ></v-text-field>
                        <span>{{errors[0]}}</span>
                    </div>
                </ValidationProvider>

                <div class="full-phone">

                    <ValidationProvider name="Area Code" rules="required" v-slot="{ errors }">
                        <div class="area">
                            <v-select
                                :items="formData.items"
                                label="Area Code"
                                outlined
                                v-model="formData.areaCode"

                            ></v-select>
                            <span>{{errors[0]}}</span>
                        </div>
                    </ValidationProvider>

                    <ValidationProvider name="Phone" rules="required|digits:7" v-slot="{ errors }">
                        <div>
                            <v-text-field
                                label="Phone"
                                type=number
                                v-model="formData.phone"
                                outlined 
                            ></v-text-field>
                            <span>{{errors[0]}}</span>
                        </div>
                    </ValidationProvider>
                </div>

                    <ValidationProvider name="Password" rules="required|max:12|min:8|alpha_num" v-slot="{ errors }">
                        <div class="input">
                            <v-text-field
                                label="Password"
                                type="password"
                                v-model="formData.password"
                                outlined
                                
                            ></v-text-field>
                            <span>{{errors[0]}}</span>
                        </div>
                    </ValidationProvider>
                <div class="submit-btn">
                    <input type="submit" tect="Submit">
                </div>
            </form>
        </ValidationObserver>
    </v-card>
</template>

<script>

export default {
    name: "Form",
    data: () => ({
        formData: {
            firstName: "",
            lastName: "",
            email: "",
            areaCode: "",
            phone: "",
            password: "",
            items: ["052", "053"]
        }
    }),
    methods: {
        onSubmit() {
            console.log(this.formData);
        },
    }
}
</script>


<style scoped>
    .card-width {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 400px !important;
        min-height: 500px;
        margin: 0 auto;
    }

    .input {
        margin: 15px;
    }
    .full-phone {
        display: flex;
        margin: 15px;
        align-content: space-around;
    }

    .area {
        /* width: 25%; */
        width: 150px;
        margin-right: 10px;

    }

    .submit-btn {
        display:flex;
        justify-content: center;
        margin-bottom: 15px;
        font-size: 20px;
        font-weight: bold;
        color:aqua;
    }
</style>