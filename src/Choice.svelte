<script>
  import {push} from 'svelte-spa-router';

  function routineOrder(){
    push('/routine/order');
  }

  function pre(){
    push('/');
  }
</script>

<div class="bg-white py-12">
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
    <div class="text-center">
      <button
        class="inline-block rounded-md border border-transparent bg-blue-500 py-3 px-8 text-center font-medium text-white hover:bg-blue-700"
        on:click="{routineOrder}"
        >루틴 시작하기</button
      >
    </div>
    <div class="text-center mt-3">
      <button
        on:click={pre}
        class="inline-block rounded-md border border-transparent bg-blue-500 py-3 px-8 text-center font-medium text-white hover:bg-blue-700"
        >루틴 불러오기</button
      >
    </div>
  </div>
</div>
