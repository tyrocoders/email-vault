<template>
    <div class="ui fixed menu" style="z-index: 1;">
        <div class="ui container">
            <router-link :to="{name: 'welcome'}" class="header item">
                <img class="logo" src="/static/images/initech.webp"/>
                &nbsp;&nbsp;Initech Message Vault
            </router-link>
            <div v-if="global.apiToken" class="header item float right" style="padding:0;">
                <div class="ui simple dropdown item">
                    <i class="large user icon"></i>
                    <i class="dropdown icon"></i>
                    <div class="menu left">
                    <div class="item" @click="logout">sign out</div>
                    <div class="item" @click="settings">settings</div>
                    <div class="item" @click="messages">messages</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
shared = require('../globalState');

module.exports = {
    data: () => ({ 
        global: shared.state,
        loggedIn: false
    }),
    methods: {
        logout: function () {
            this.global.apiToken = null;
        },
        settings: function () {
            this.$router.push({ name: 'settings' });
        },
        messages: function () {
            this.$router.push({ name: 'messages' });
        }
    }
}
</script>