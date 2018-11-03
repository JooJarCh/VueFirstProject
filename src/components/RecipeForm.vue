<template>
    <div>
        <form @submit.prevent="" class="form-horizontal">
            <fieldset>

                <!-- Form Name -->
                <legend>Recipe Name</legend>
                <pre>{{recipe}}</pre>

                <!-- Text input-->
                <div class="form-group row">
                    <label class="col-md-3 control-label" for="Title">Title</label>
                    <div class="col-md-4">
                        <input id="title" name="Title" v-model="recipe.title" type="text" placeholder="" class="form-control input-md">

                    </div>
                </div>

                <!-- Text input-->
                <div class="form-group row">
                    <label class="col-md-3 control-label" for="Image_url">Image URL</label>
                    <div class="col-md-4">
                        <input id="image_url" name="Image_url" v-model="recipe.image_url" type="text" placeholder="" class="form-control input-md">

                    </div>
                </div>

                <button type="button" class="btn btn-info" @click="addIngredient">
                    <i class="fa fa-plus-circle">more Ingredient</i>
                </button>
                <!-- Text input-->
                <div class="form-group row">
                    <label class="col-md-3 control-label" for="txtIngredient" >Ingredient</label>
                    <div class="col-md-4">
                        <div v-for="(ingredient,index) in recipe.ingredient" :key="index">
                            <input v-model="recipe.ingredient[index]" 
                            type="text" class="form-control input-md">
                        </div>
                    </div>
                </div>

                <!-- Text input-->
                <div class="form-group row">
                    <label class="col-md-3 control-label" for="description">Description</label>
                    <div class="col-md-4">
                        <input id="description" name="description" v-model="recipe.description" type="text" placeholder="" class="form-control input-md">

                    </div>
                </div>

                <!-- Button (Double) -->
                <div class="form-group">
                    <label class="col-md-3 control-label" for="summit"></label>
                    <div class="col-md-4 col-md-6">
                        <button @click="save" id="summit" name="summit" class="btn btn-success">Summit</button>
                        <button id="cancel" name="cancel" class="btn btn-danger">Cancel</button>
                    </div>
                </div>

            </fieldset>
        </form>

    </div>
</template>

<script>
export default {
    data () {
        return {
            recipe: {
                title: '',
                image_url: '',
                description: '',
                ingredient: ['']
            }
        }

    }, methods: {
        addIngredient () {
            this.recipe.ingredient.push('')

        },
        save () {
            this.$emit('saveRecipe', this.recipe)

        }
    },
}
</script>

<style scoped>
</style>