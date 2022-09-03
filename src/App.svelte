<script>
  import Router from "svelte-spa-router";
  import Home from "./Home.svelte";
  import RoutineOrder from "./routine/RoutineOrder.svelte";
  import RoutineSetting from "./routine/RoutineSetting.svelte";
</script>

<div class="py-12">
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
    <div class="text-center">
      <p
        class="mt-2 text-3xl font-bold leading-8 tracking-tight text-blue-400 sm:text-4xl"
      >
        O.un
      </p>
    </div>
  </div>
</div>

<Router
  routes={{
    "/": Home,
    "/routine/order": RoutineOrder,
    "/routine/setting": RoutineSetting,
  }}
/>
