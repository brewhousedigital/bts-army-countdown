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
  <h2>{name} {#if daysRemaining > 0 && percentDifference > 0}<small>{percentDifference}% complete, {daysRemaining} days remaining</small>{/if}</h2>


  <div class="progress-container">
    <div class="progress-bar" style="background-color: {color}; width: {percentDifference}%"></div>
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

  h2 small {
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

  .icon {
    max-width: 70px;
    position: absolute;
    top: 25px;
  }
</style>
