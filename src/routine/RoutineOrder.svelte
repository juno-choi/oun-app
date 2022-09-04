<script>
  import { routines } from "../store/routines";

  const routinePlaceholder = "운동을 입력해주세요.";
  const routineBtnText = "-";
  const routineInputClass =
    "shadow appearance-none border rounded py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline mr-0";
  const routineBtnClass =
    "bg-gray-500 hover:bg-gray-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline";

  let RoutineObject = class RoutineObject {
    constructor(routine) {
      this.routine = routine;
    }
  };

  function routineRemove() {
    // idx가 1일 경우 삭제 불가
    const length = document
      .getElementById("routine-div")
      .querySelectorAll("input").length;
    if (length < 2) {
      alert("루틴을 모두 제거할 수 없습니다.");
      return;
    }

    this.parentElement.remove();
  }

  function routineAdd() {
    const target = document.getElementById("routine-div");
    const div = document.createElement("div");
    div.setAttribute("class", "mb-4");

    const input = document.createElement("input");
    input.setAttribute("class", routineInputClass);
    input.setAttribute("type", "text");
    input.setAttribute("placeholder", routinePlaceholder);

    const button = document.createElement("button");
    button.setAttribute("class", routineBtnClass);
    button.setAttribute("type", "button");
    button.innerText = routineBtnText;
    button.addEventListener("click", routineRemove);

    div.appendChild(input);
    div.appendChild(button);
    target.appendChild(div);
  }

  function routineComplete() {
    const routineList = [];
    document
      .getElementById("routine-div")
      .querySelectorAll("input")
      .forEach((input) => {
        routineList.push(new RoutineObject(input.value));
      });
    routines.update((routine) => (routine = routineList));
  }
</script>

<div class="bg-white py-12">
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
    <div class="text-center">
      <p
        class="text-3xl font-bold leading-8 tracking-tight text-gray-400 sm:text-4xl"
      >
        🏃‍♂️ 운동 루틴을 지정해주세요.
      </p>
    </div>

    <div id="routine-div" class="text-center mt-10">
      <div class="mb-4">
        <input
          class={routineInputClass}
          type="text"
          placeholder={routinePlaceholder}
        />
        <button class={routineBtnClass} type="button" on:click={routineRemove}>
          {routineBtnText}
        </button>
      </div>
    </div>
    <div class="text-center mt-4">
      <div class="items-center">
        <button
          class="bg-gray-500 hover:bg-gray-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          type="button"
          on:click={routineAdd}
        >
          + 루틴 추가
        </button>
      </div>
    </div>

    <div class="text-center mt-10">
      <a
        href="/#"
        class="inline-block rounded-md border border-transparent bg-blue-500 py-3 px-8 text-center font-medium text-white hover:bg-blue-700"
        >이전</a
      >
      <a
        href="/#/routine/setting"
        class="inline-block rounded-md border border-transparent bg-blue-500 py-3 px-8 text-center font-medium text-white hover:bg-blue-700"
        on:click={routineComplete}>다음</a
      >
    </div>
  </div>
</div>
