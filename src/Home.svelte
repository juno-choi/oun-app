<script>
  function gettingReady() {
    alert("해당 기능은 준비 중입니다...");
  }
</script>

<div class="bg-white py-12">
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
    <div class="text-center">
      <a
        href="/#/routine/order"
        class="inline-block rounded-md border border-transparent bg-blue-500 py-3 px-8 text-center font-medium text-white hover:bg-blue-700"
        >운동 시작하기</a
      >
    </div>
    <div class="text-center mt-3">
      <a
        href="/#"
        on:click={gettingReady}
        class="inline-block rounded-md border border-transparent bg-blue-500 py-3 px-8 text-center font-medium text-white hover:bg-blue-700"
        >루틴 불러오기</a
      >
    </div>
  </div>
</div>
