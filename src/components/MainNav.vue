<template>
    <b-navbar type="is-dark" fixed-top wrapper-class="container">
        <template slot="brand">
            <b-navbar-item tag="router-link" :to="{ name: 'home' }">
                <img src="../assets/logo.png" alt="Ellaism"/>
            </b-navbar-item>
        </template>
        <template slot="start">
            <b-navbar-item tag="router-link" :to="{ name: 'home' }">
                Home
            </b-navbar-item>
            <b-navbar-dropdown label="Stats" hoverable>
                <b-navbar-item tag="router-link" :to="{ name: 'richest' }">
                    Rich List
                </b-navbar-item>
            </b-navbar-dropdown>
            <b-navbar-dropdown label="Community" hoverable>
                <b-navbar-item href="https://ellaism.io">
                    Ellaism Website
                </b-navbar-item>
                <b-navbar-item href="https://github.com/ellaism" rel="nofollow">
                    Ellaism GitHub
                </b-navbar-item>
                <hr class="dropdown-divider">
                <b-navbar-item href="https://discordapp.com/invite/gz9tURY" rel="nofollow">
                    Discord
                </b-navbar-item>
                <b-navbar-item href="https://www.reddit.com/r/ellaism/" rel="nofollow">
                    Reddit
                </b-navbar-item>
                <b-navbar-item href="https://t.me/ellaismcoin" rel="nofollow">
                    Telegram
                </b-navbar-item>
                <b-navbar-item href="https://twitter.com/EllaismCore" rel="nofollow">
                    Twitter
                </b-navbar-item>
            </b-navbar-dropdown>
        </template>
        <template slot="end">
            <b-navbar-item tag="div">
                <MainNavSearch/>
            </b-navbar-item>
        </template>
    </b-navbar>
</template>

<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';
import MainNavSearch from '@/components/MainNavSearch.vue';

@Component({
    components: {
        MainNavSearch,
    },
})
export default class MainNav extends Vue {
}
</script>
