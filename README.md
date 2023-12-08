# Final-Project
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>New Year Countdown</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
    }

    .countdown {
      margin-top: 100px;
    }

    h1 {
      font-size: 2em;
    }

    #timer {
      font-size: 3em;
      color: #333;
    }
  </style>
</head>
<body>
  <div class="countdown">
    <h1>New Year Countdown</h1>
    <p id="timer"></p>
  </div>

  <script>
    function getTimeRemaining(endTime) {
      const total = Date.parse(endTime) - Date.parse(new Date());
      const seconds = Math.floor((total / 1000) % 60);
      const minutes = Math.floor((total / 1000 / 60) % 60);
      const hours = Math.floor((total / (1000 * 60 * 60)) % 24);
      const days = Math.floor(total / (1000 * 60 * 60 * 24));

      return {
        total,
        days,
        hours,
        minutes,
        seconds
      };
    }

    function initializeClock(id, endTime) {
      const clock = document.getElementById(id);
      const timeinterval = setInterval(() => {
        const t = getTimeRemaining(endTime);
        clock.innerHTML = `${t.days} days ${t.hours} hours ${t.minutes} minutes ${t.seconds} seconds`;

        if (t.total <= 0) {
          clearInterval(timeinterval);
          clock.innerHTML = 'Happy New Year!';
        }
      }, 1000);
    }

    const deadline = '2024-01-01T00:00:00'; // Change this to the desired New Year's date
    initializeClock('timer', deadline);
  </script>
</body>
</html>
