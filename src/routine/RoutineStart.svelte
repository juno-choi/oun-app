<script>
  import { routines } from "../store/routines";

  const routineList = [];
  let hour = 0;
  let minute = 0;
  let second = 0;
  const interval = setInterval(() => {
    second++;
    if (second == 60) {
      second = 0;
      minute++;
    }
    if (minute == 60) {
      minute = 0;
      hour++;
    }
  }, 1000);
  let routineName = "[운동 이름]";
  let routineCnt = 0;
  let setCnt = 0;
  let routineStrList = [
    "시작해요👏",
    "힘내세요💪",
    "거의 다 왔어요😄",
    "마지막 세트에요😍",
  ];
  let routineStr = routineStrList[0];
  const storeList = { $routines }.$routines;
  storeList.forEach((s) => {
    routineList.push(s);
  });

  //routine 이름 초기화
  routineName = storeList[0].routine;

  function routineClick() {
    setCnt++;
    routineStrCheck();
    const set = storeList[routineCnt].set;
    if (set == setCnt) nextSet();
  }

  function routineStrCheck() {
    const set = storeList[routineCnt].set;
    const cnt = setCnt / set;
    console.log(cnt);
    if (setCnt > 0) routineStr = routineStrList[1];
    if (cnt >= 0.6) routineStr = routineStrList[2];
    if (setCnt == set - 1) routineStr = routineStrList[3];
  }

  function nextSet() {
    routineCnt++;
    setCnt = 0;
    routineStr = routineStrList[0];
    //운동이 끝났는지 체크
    if (routineCnt >= storeList.length) {
      alert(
        "운동 종료! 고생하셨습니다👏 \n 총 소요 시간 = " +
          hour +
          "시간 " +
          minute +
          "분 " +
          second +
          "초"
      );
      routineCnt = 0;
      clearInterval(interval);
      //종료 화면으로 넘어가기
      window.location.href = "/";
      return;
    }
    routineName = storeList[routineCnt].routine;
  }

  console.log(routineList);
</script>

<div class="max-w grid lg:grid-cols-3 grid-cols-1 content-center">
  <div />
  <div
    class="max-w rounded overflow-hidden shadow-lg bg-blue-400 text-white "
    on:click={routineClick}
  >
    <div class="px-6 py-4 text-center content-center">
      <div class="text-3xl font-bold leading-8 tracking-tight sm:text-4xl mb-2">
        🏃‍♂️ {routineName}
      </div>
      <div class="text-4xl font-bold leading-8 tracking-tight mb-2 mt-10">
        {setCnt}
      </div>
      <div
        class="text-xl sm:text-2xl font-bold leading-8 tracking-tight mb-2 mt-10"
      >
        터치하면 카운터가 올라가요! {routineStr}
      </div>
      <div class="text-4xl font-bold leading-8 tracking-tight mb-2 mt-10">
        루틴 소요 시간 : {hour} h : {minute} m : {second} s
      </div>
    </div>
    <div class="px-6 pt-4 pb-2">
      {#each routineList as { routine }}
        <span
          class="inline-block bg-blue-500 rounded-full px-3 py-1 text-sm font-semibold text-white-700 mr-2 mb-2"
          >#{routine}</span
        >
      {/each}
    </div>
  </div>
</div>
