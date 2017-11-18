<template>
    <a class="fixo button is-large is-danger is-loading" v-show="isLoading">Loading</a>
    <div class="container">
        <h1 class="title">Bitcoin</h1>

        <div class="columns">
            <div class="column is-12">
                <table class="table">
                    <thead>
                    <th>Date</th>
                    <th>Buy</th>
                    <th>Sell</th>
                    <th>Variation</th>


                    </thead>
                    <tbody>
                    <tr v-for="quotation in quotations">
                        <td>{{quotation.date}}</td>
                        <td>{{quotation.buy}}</td>
                        <td>{{quotation.sell}}</td>
                        <td>{{quotation.variation}}</td>

                    </tr>
                    </tbody>
                </table>

            </div>
        </div>

    </div>


</template>
<script>

    export default {
        data () {
            return {
                isLoading: false,
                title: 'Vue.js Crud',
                search: '',
                quotations: [],
                page: 1,
                total: 0,
                selected: {},
                itensPerPage: 10
            }
        },
        methods: {
            showLoading(){
                this.isLoading=true;
            },
            hideLoading(){
                this.isLoading=false;
            },
            loadBreweries(){

                let t = this
                this.showLoading()

                let start = (this.page * this.itensPerPage) - (this.itensPerPage - 1)
                let end = this.page * this.itensPerPage



                this.$http.get(`https://geek-back.herokuapp.com/bitcoin/`, { headers: {'Accept': 'application/json'}}).then(
                    response=>{
                        t.quotations = response.body

                    },
                    error=>{
                        console.log(error)
                    }).finally(function () {
                    t.hideLoading();
                })

            },
            searchBreweries(){

            }
        },
        created(){
            this.loadBreweries();
        },


    };




</script>
<style>
    .fixo{float: right; margin-right: 10px; margin-top: 0px; z-index: 1000;}
</style>