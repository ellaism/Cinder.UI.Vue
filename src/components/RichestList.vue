<template>
    <div v-if="addresses !== null" class="table-container">
        <b-table class="is-striped is-hoverable is-fullwidth" :data="addresses">
            <template slot-scope="props">
                <b-table-column field="hash" label="Address">
                    <router-link :to="{ name: 'address', params: { hash: props.row.hash }}">{{ props.row.hash }}</router-link>
                </b-table-column>
                <b-table-column field="balance" label="Balance">
                    {{ props.row.balance }}
                </b-table-column>
            </template>
            <template slot="empty">
                <section class="section">
                    <div class="content has-text-grey has-text-centered">
                        <p>No addresses found.</p>
                    </div>
                </section>
            </template>
        </b-table>
    </div>
</template>

<script lang="ts">
import {Component, Vue, Prop} from 'vue-property-decorator';
import Richest from '@/models/Richest';

@Component
export default class RichestList extends Vue {
    @Prop()
    public readonly addresses?: Richest[];
}
</script>
