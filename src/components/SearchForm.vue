<template>
    <div class="col-12 navbar-brand navbar-light bg-light navbar" style="margin-top: 10px; margin-bottom: 10px; min-width: 750px;">
        <h3 style="margin-bottom: 20px">Search Posts (Sorted by New)</h3> 
        <div class="row">
            <div class="col-2">
                <input type="text" name="country" placeholder="Country" value="" class="form-control">
            </div>
            <div class="col-2">
                <select name="cat" id="cat" class="form-control">
                    <option selected="" value="">any</option>
                    <option value="sell">sellers</option>
                    <option value="buy">buyers</option>
                    <option value="trade">traders</option>
                </select>
            </div>
            <div class="col-6">
                <input class="form-control" v-on:input="$emit('updateSearch', $event.target.value)">
            </div>
            <div class="col-2">
                <input class="btn btn-primary" type="submit" value="Submit">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SearchForm'
}
</script>