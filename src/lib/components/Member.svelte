<script>
  import dayjs from "dayjs";

  export let name = "";
  export let start = "";
  export let end = "";
  export let color = "";
  export let icon = "";

  const currentDate = dayjs();
  const startDate = dayjs(start);
  const endDate = dayjs(end);

  let totalDaysRequired = endDate.diff(startDate, "day")
  if(isNaN(totalDaysRequired)) totalDaysRequired = 0

  let daysCurrentlyServed = currentDate.diff(startDate, "day")
  if(isNaN(daysCurrentlyServed)) daysCurrentlyServed = 0

  let percentDifference = Math.ceil((daysCurrentlyServed / totalDaysRequired) * 100)
  if(isNaN(percentDifference)) percentDifference = 0

  let daysRemaining = totalDaysRequired - daysCurrentlyServed;
</script>



<div class="container">
  <div class="name">
    <h2>{name}</h2>
    {#if daysRemaining > 0 && percentDifference > 0}<small>{daysRemaining} days remaining</small>{/if}
  </div>


  <div class="progress-container">
    <div class="progress-bar" style="background-color: {color}; width: {percentDifference}%">
      <span>{percentDifference}%</span>
    </div>
  </div>


  <img
    src={`/images/${icon}.png`}
    alt=""
    class="icon"
    style="left: calc({percentDifference}% - 35px)" />
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

  .name h2 {
    margin: 0;
  }

  .name small {
    font-style: italic;
    font-size: 70%;
  }

  progress {
    width: 100%;
  }

  .progress-container {
    background-color: #eee;
    border-radius: 8px;
    overflow: hidden;
  }

  .progress-bar {
    height: 8px;
    width: 25%;
  }

  .progress-bar span {
    font-size: 6px;
    display: block;
    padding-left: 7px;
  }

  .icon {
    max-width: 70px;
    position: absolute;
    top: 20px;
  }
</style>
