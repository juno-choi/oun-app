<script>
  import { routines } from "../store/routines";

  let RoutineObject = class RoutineObject {
    constructor(routine, set, ea) {
      this.routine = routine;
      this.set = set;
      this.ea = ea;
    }
  };

  const routineList = [];
  const storeList = { $routines }.$routines;
  storeList.forEach((s) => {
    routineList.push(s);
  });

  function routineComplete() {
    const routineList = [];
    document
      .getElementById("routine-div")
      .querySelectorAll("div")
      .forEach((div) => {
        const inputs = div.querySelectorAll("input");
        routineList.push(
          new RoutineObject(inputs[0].value, inputs[1].value, inputs[2].value)
        );
      });
    routines.update((routine) => (routine = routineList));
  }
</script>

<ul />

<div class="bg-white py-12">
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
    <div class="text-center">
      <p
        class="text-3xl font-bold leading-8 tracking-tight text-gray-400 sm:text-4xl"
      >
        🏃‍♂️ 루틴 세트와 개수를 지정해주세요.
      </p>
    </div>

    <div id="routine-div" class="text-center mt-10">
      {#each routineList as { routine }, i}
        <div class="mb-4">
          <input
            class="w-40 shadow appearance-none border rounded py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline mr-0"
            type="text"
            value={routine}
            disabled
          />

          <input
            class="w-24 shadow appearance-none border rounded py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline mr-0"
            type="text"
            placeholder="세트"
          />
          <input
            class="w-24 shadow appearance-none border rounded py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline mr-0"
            type="text"
            placeholder="세트당 수"
          />
        </div>
      {/each}
    </div>

    <div class="text-center mt-10">
      <a
        href="/#/routine/order"
        class="inline-block rounded-md border border-transparent bg-blue-500 py-3 px-8 text-center font-medium text-white hover:bg-blue-700"
        >이전</a
      >
      <a
        href="/#/routine/start"
        class="inline-block rounded-md border border-transparent bg-blue-500 py-3 px-8 text-center font-medium text-white hover:bg-blue-700"
        on:click={routineComplete}>다음</a
      >
    </div>
  </div>
</div>
