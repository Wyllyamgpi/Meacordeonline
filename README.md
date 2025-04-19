# Meacordeonline
Despertador online 
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Despertador Online</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 40px;
      background: #f0f0f0;
    }
    h1 {
      margin-bottom: 20px;
    }
    #clock {
      font-size: 48px;
      margin-bottom: 20px;
    }
    input, button {
      font-size: 18px;
      padding: 10px;
      margin: 5px;
    }
  </style>
</head>
<body>
  <h1>Despertador Online</h1>
  <div id="clock"></div>
  <input type="time" id="alarmTime">
  <button onclick="setAlarm()">Ativar Alarme</button>
  <audio id="alarmSound" src="https://www.soundjay.com/clock/sounds/alarm-clock-1.mp3" preload="auto"></audio>

  <script>
    const clock = document.getElementById('clock');
    const alarmSound = document.getElementById('alarmSound');
    let alarmTime = null;
    let alarmTimeout = null;

    function updateClock() {
      const now = new Date();
      const timeString = now.toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit', second: '2-digit' });
      clock.textContent = timeString;

      if (alarmTime && timeString === alarmTime + ':00') {
        alarmSound.play();
        alert('Hora de acordar!');
        alarmTime = null;
      }
    }

    function setAlarm() {
      const inputTime = document.getElementById('alarmTime').value;
      if (!inputTime) {
        alert('Por favor, defina um horário para o alarme.');
        return;
      }
      alarmTime = inputTime;
      alert('Alarme definido para ' + alarmTime);
    }

    setInterval(updateClock, 1000);
    updateClock();
  </script>
</body>
</html>
