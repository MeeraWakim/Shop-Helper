<template>
    <Page class="page">
        <ActionBar title="Home" class="action-bar" />
        <ScrollView>
            <StackLayout class="home-panel">
                <!--Add your page content here-->
                <Label text="Shopping List" />
                <ListView class="list-group" for="country in countries"
                    @itemTap="onItemTap" style="height:1250px">
                    <v-template>
                        <FlexboxLayout flexDirection="row" class="list-group-item">
                            <Image :src="country.imageSrc" class="thumb img-circle" />
                            <TextField v-model="textFieldValue1" hint="Enter text..." />
                            style="width: 100%" />
                        </FlexboxLayout>
                    </v-template>
                </ListView>

                <Button text="Button" @tap="onButtonTap" class="h1 description-label" />
            </StackLayout>
        </ScrollView>


    </Page>

    data() {
    return{
    textvalue: '',
    }
    };


</template>

<script>
    export default {
        methods: {
            onItemTap: function(args) {
                console.log("Item with index: " + args.index + " tapped");
            },

            onButtonTap() {
                console.log("Button was pressed");
            }
        },

        data() {
            return {
                countries: [{
                        name: "Item 1",
                        imageSrc: "https://cdn1.iconfinder.com/data/icons/get-me-home/512/square_blank_check_empty-512.png"
                    },

                    {
                        name: "Item 2",
                        imageSrc: "https://cdn1.iconfinder.com/data/icons/get-me-home/512/square_blank_check_empty-512.png"
                    },

                    {
                        name: "Item 3",
                        imageSrc: "https://cdn1.iconfinder.com/data/icons/get-me-home/512/square_blank_check_empty-512.png"
                    },

                    {
                        name: "Item 4",
                        imageSrc: "https://cdn1.iconfinder.com/data/icons/get-me-home/512/square_blank_check_empty-512.png"
                    },

                    {
                        name: "Item 5",
                        imageSrc: "https://cdn1.iconfinder.com/data/icons/get-me-home/512/square_blank_check_empty-512.png"
                    }
                ],

                textFieldValue: ""
            };
        }
    };
</script>

<style scoped>
    .home-panel {
        vertical-align: center;
        font-size: 20;
        margin: 15;
    }

    .description-label {
        margin-bottom: 2;
    }
</style>