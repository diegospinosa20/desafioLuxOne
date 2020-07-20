<template>
    <div class="container">
        <div class="row">
            <div class="col-md-6">
                <p id="nome">{{ repo.name }}</p>
                <p id="stars"><b-icon-star style="color: #000;"></b-icon-star> {{ repo.stargazers_count }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["repo"]
}
</script>

<style>

#nome {
    font-size: 30px;
}

#stars {
    font-size: 20px;
}

</style>