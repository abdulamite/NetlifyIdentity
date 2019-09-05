<template>
  <h1>Bravo! You made it! Protected Page</h1>
</template>

<script>
  import swal from "sweetalert2";
  export default {
    name: "Protected",
    beforeRouteEnter: (to, from, next) => {
      next(vm => {
        console.log(vm.$store.state.user.user);
        if (vm.$store.state.user.user) {
          return next();
        } else {
          swal({
            title: "Shit looking real broken to me!",
            text: "Please log in or sign up!",
            type: "error",
            allowOutsideClick: true,
            confirmButtonText: "Well damn okay"
          });
          return next({ name: "Home" });
        }
      });
    }
  };
</script>