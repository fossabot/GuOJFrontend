<template>
    <v-container class="fill-height justify-center align-center my-6">
        <v-card color="primary" dark style="max-width:550px;" class="pa-3">
            <div class="d-flex grow flex-wrap">
                    <v-sheet
                        class="text-start v-card--material__heading mb-n6 pa-7"
                        dark
                        width="auto"
                        max-height="90"
                        elevation="6"
                        color="cyan"
                    >
                        <v-icon size="32">mdi-account-multiple</v-icon>
                    </v-sheet>
                    <v-card-title>
                        <span>注册</span>
                    </v-card-title>
                    <div class="flex-grow-1"></div>
                </div>
            <v-divider></v-divider>
            <v-container>
                <v-container>
                    <v-form ref="form" v-model="valid">
                        <v-row>
                            <v-text-field
                                prepend-inner-icon="mdi-account-circle"
                                label="用户名"
                                :rules="[rules.required]"
                                :value="username"
                                v-model="username"
                            ></v-text-field>
                        </v-row>
                        <v-row>
                            <v-text-field
                                prepend-inner-icon="mdi-email"
                                label="邮箱"
                                :rules="[rules.required]"
                                :value="email"
                                v-model="email"
                            ></v-text-field>
                        </v-row>
                        <v-row>
                            <v-text-field
                                prepend-inner-icon="mdi-key-outline"
                                :append-icon="show ? 'visibility' : 'visibility_off'"
                                :rules="[rules.required,rules.min]"
                                :type="show ? 'text' : 'password'"
                                label="密码"
                                hint="至少8个字符"
                                :value="password"
                                v-model="password"
                                class="input-group--focused"
                                @click:append="show = !show"
                            ></v-text-field>
                            <v-text-field
                                prepend-inner-icon="mdi-key-outline"
                                :rules="[rules.required,rules.min]"
                                type="password"
                                label="重复密码"
                                hint="至少8个字符"
                                :value="password_repeat"
                                v-model="password_repeat"
                                class="input-group--focused"
                            ></v-text-field>
                        </v-row>
                        <v-row></v-row>
                    </v-form>
                    <v-row>
                        <v-col>
                            <v-btn block :disabled="!valid" color="success" @click="Register">注册</v-btn>
                        </v-col>
                    </v-row>
                </v-container>
            </v-container>
        </v-card>
    </v-container>
</template>

<script lang="ts">
import Vue from 'vue';
import axios from '../api/session';
import auth from '../api/auth';
export default Vue.extend({
    components: {},
    data: () => {
        return {
            valid: true,
            show: false,
            email: '',
            username: '',
            password: '',
            password_repeat: '',
            rules: {
                required: (value: String) => !!value || '必填',
                min: (value: String) => value.length >= 8 || '至少8个字符'
            }
        };
    },
    methods: {
        Register() {
            const email = this.email;
            const username = this.username;
            const password = this.password;
            const password_repeat = this.password_repeat;
            //this.$store.dispatch('Login',{username,password}).then(()=>this.$router.push('/'))
        }
    }
});
</script>

<style lang="css">
.v-card--material__heading 
{
    position: relative;
    top: -40px;
    transition: 0.3s ease;
    z-index: 1;
}
</style>