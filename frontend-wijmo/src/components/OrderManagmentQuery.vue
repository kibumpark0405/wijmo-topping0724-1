<template>
    <v-card outlined style="border-radius: 0; max-height:15vh; margin-top:-10px; padding-bottom:10px;">
        <v-card-title>
            OrderManagment
        </v-card-title>
    
        <v-card-text>
            <v-row no-gutters style="margin: 15px 0px -30px -15px;">
                <v-col style="max-width:140px;">
                    <PersonInChargeId offline label="PersonInChargeId" v-model="value.parameters.personInChargeId" :editMode="editMode" @change="change"/>
                </v-col>
                <v-col>
                    <v-btn class="gs-query-search-btn"
                        @click="search"
                        flat
                        small
                        color="primary"
                    >
                        <v-icon small>mdi-magnify</v-icon>검색
                    </v-btn>
                </v-col>
            </v-row>
        </v-card-text>
    </v-card>
</template>

<script>
    export default {
        name: 'OrderManagmentQuery',
        components:{},
        props: {},
        data: () => ({
            editMode: true,
            value: {
                apiPath: 'findByPersonInCharge',
                parameters: {}
            },
        }),
        created() {
            this.value.parameters.personInChargeId = {};
        },
        watch: {
        },
        methods: {
            search() {
                let search = null;
                if((this.value.parameters.personInChargeId.id == '' || typeof(this.value.parameters.personInChargeId) == 'object')) {
                    search = null;
                }else{
                    search = this.value;
                }
                this.$emit('search', search);
            },
            close() {
                this.$emit('closeDialog');
            },
            change() {
                this.$emit('input', this.value);
            },
        }
    }
</script>
<style>
.attributes-list{
    margin-left: 15px;
}
</style>

