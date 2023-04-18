<script>
  import dayjs from "dayjs";

  export let name = "";
  export let start = "";
  export let end = "";
  export let color = "";
  export let icon = "";

  let currentDate = dayjs();
  // The start date needs to have 1 removed or the person starting will never cross 1% on the chart
  let startDate = dayjs(start).subtract(1, 'day');
  let endDate = dayjs(end);

  let totalDaysRequired = endDate.diff(startDate, "day")
  if(isNaN(totalDaysRequired)) totalDaysRequired = 0

  let daysCurrentlyServed = currentDate.diff(startDate, "day")
  if(isNaN(daysCurrentlyServed)) daysCurrentlyServed = 0

  let percentDifference = Math.ceil((daysCurrentlyServed / totalDaysRequired) * 100)
  if(isNaN(percentDifference)) percentDifference = 0
  if(percentDifference >= 100) percentDifference = 100;

  let daysRemaining = totalDaysRequired - daysCurrentlyServed;
</script>



<div class="container">
  <div class="name {daysRemaining === 0 && percentDifference === 100 ? 'done' : ''}">
    <h2 style="color: {color}">{name}</h2>
    {#if daysRemaining > 0 && percentDifference > 0}
      <div class="time-remaining">
        <div>{percentDifference}% complete</div>
        <div>{daysRemaining} day{daysRemaining > 1 ? 's' : ''} remaining</div>
      </div>
    {/if}

    {#if daysRemaining === 0 && percentDifference === 100}
      <div class="">
        <div>Came Home 🎉</div>
      </div>
    {/if}
  </div>


  {#if percentDifference > 0}
    <div class="progress-container">
      <div class="progress-bar" style="background-color: {color}; width: {percentDifference}%"></div>
    </div>
  {:else}
    <div class="progress-container">
      <div class="progress-bar" style="background-color: {color};"></div>
    </div>
  {/if}



  {#if percentDifference > 0 && percentDifference < 100}
    <img
      src={`/images/${icon}.png`}
      alt=""
      class="icon"
      style="left: calc({percentDifference}% - 37px)" />
  {/if}

  {#if percentDifference <= 0}
    <img
      src={`/images/${icon}-start.png`}
      alt=""
      class="icon start"
      style="left: calc({percentDifference}% - 35px)" />
  {/if}

  {#if percentDifference === 100}
    <img
      src={`/images/${icon}-end.png`}
      alt=""
      class="icon end"
      style="left: calc({percentDifference}% - 35px)" />
  {/if}

</div>



<style>
  .container {
    position: relative;
    margin-bottom: 45px;
  }

  .name {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    margin-bottom: 13px;
  }

  .name.done {
    justify-content: start;
    gap: 7px;
    font-size: 24px;
    font-weight: 700;
  }

  .name h2 {
    margin: 0;
  }

  .name.done h2 {
    font-size: 24px;
  }

  .name .time-remaining {
    font-style: italic;
    font-size: 70%;
    text-align: right;
  }

  progress {
    width: 100%;
  }

  .progress-container {
    background-color: #eee;
    border-radius: 8px;
    overflow: hidden;
    position: relative;
  }

  .progress-bar {
    height: 8px;
    width: 0;
  }

  .progress-bar span {
    font-size: 6px;
    display: block;
    padding-left: 7px;
  }

  .icon {
    max-width: 70px;
    position: absolute;
    top: 17px;
  }

  .icon.start {
    top: 17px;
  }

  .icon.end {
    top: 13px;
  }
</style>
