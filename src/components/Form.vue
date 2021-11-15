<template>
    <v-card
    class="card-width"
    elevation="2"
    outlined
    >
        <ValidationObserver v-slot="{ handleSubmit }">
            <form @submit.prevent="handleSubmit(onSubmit)">
                <ValidationProvider name="First Name" rules="required|alpha" v-slot="{ errors }">
                    <div>
                        <v-text-field
                            label="First Name"
                            type="text"
                            v-model="formData.firstName"
                            outlined
                            class="input"
                        ></v-text-field>
                        <span>{{errors[0]}}</span>
                    </div>
                </ValidationProvider>

                <ValidationProvider name="Last Name" rules="required|alpha" v-slot="{ errors }">
                    <div>
                        <v-text-field
                            label="Last Name"
                            type="text"
                            v-model="formData.lastName"
                            outlined
                            class="input"
                        ></v-text-field>
                        <span>{{errors[0]}}</span>
                    </div>
                </ValidationProvider>

                <ValidationProvider name="Email" rules="required|email" v-slot="{ errors }">
                    <div>
                        <v-text-field
                            label="Email"
                            type="email"
                            v-model="formData.email"
                            outlined
                            class="input"
                        ></v-text-field>
                        <span>{{errors[0]}}</span>
                    </div>
                </ValidationProvider>

                <div class="full-phone">

                    <ValidationProvider name="Area Code" rules="required" v-slot="{ errors }">
                        <div>
                            <v-select
                                :items="formData.items"
                                label="Area Code"
                                outlined
                                class="area"
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
                                class="phone"
                            ></v-text-field>
                            <span>{{errors[0]}}</span>
                        </div>
                    </ValidationProvider>
                </div>

                <ValidationProvider name="Password" rules="required|max:12|min:8|alpha_num" v-slot="{ errors }">
                            <div>
                                <v-text-field
                                    label="Password"
                                    type="password"
                                    v-model="formData.password"
                                    outlined
                                    class="input"
                                ></v-text-field>
                                <span>{{errors[0]}}</span>
                            </div>
                        </ValidationProvider>
                <input type="submit" tect="Submit">
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
        width: 400px;
        min-height: 500px;
        margin: 0 auto
    }

    .input {
        width: 90%;
    }
    .full-phone {
        display: flex
    }

    .area {
        width: 25%;
        margin-right: 10px;
        border: 1px sold black;
        width: 80px;
        height: 60px;
    }

    .phone {
        width: 55%
    }
</style>