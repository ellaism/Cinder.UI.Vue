import {SortType} from "@/models/SortType";
<template>
    <div v-if="isLoading">
        <PageLoader/>
    </div>
    <div v-else-if="addresses !== null" class="richest-page">
        <h1 class="title is-4 is-spaced">Richest Ellaism Addresses</h1>
        <RichestList :addresses="addresses"/>
    </div>
</template>

<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';
import RichestList from '@/components/RichestList.vue';
import PageLoader from '@/components/PageLoader.vue';
import CinderApiService from '@/services/CinderApiService';
import store from '@/Store';
import {mapState} from 'vuex';
import Richest from '@/models/Richest';

@Component({
    components: {
        PageLoader,
        RichestList,
    },
    computed: mapState([
        'isLoading',
    ]),
})
export default class RichestPage extends Vue {
    public isLoading!: boolean;
    public addresses: Richest[] | null = null;
    private api = new CinderApiService();

    public async created() {
        await this.getRichest();
    }

    private async getRichest(): Promise<void> {
        store.commit('toggleLoader', true);
        try {
            const data = await this.api.getRichest(1, 100);
            this.addresses = data.items;
        } catch (e) {
        }
        store.commit('toggleLoader', false);
    }
}
</script>
