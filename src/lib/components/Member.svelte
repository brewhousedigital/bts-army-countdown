<script>
  import dayjs from "dayjs";

  export let name = "";
  export let start = "";
  export let end = "";

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

  <progress
    id={`progress bar for ${name}`}
    max="100"
    value={percentDifference}>{percentDifference}%</progress>

  <div></div>
</div>



<style>
  .container {
    position: relative;
    margin-bottom: 45px;
  }

  h2 small {
    font-style: italic;
    font-size: 60;
  }

  progress {
    width: 100%;
  }

  progress::-moz-progress-bar { background: blue; }
  progress::-webkit-progress-value { background: blue; }
  progress { color: blue; }
</style>
