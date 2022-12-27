<!-- Não estou usando este metodo, em breve farei algo com ela -->
<template>
  <div class="card card-body-mb-2">
    <div class="row">
      <div class="col-md-6">
        <a href target="_black">{{ repo.name }}</a>
      </div>
      <div class="col-md-6">
        <span class="badga badga-primary"></span>
        <span class="badga badga-secondary"></span>
        <span class="badga badga-sucess"></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["repo"]
};
</script>
